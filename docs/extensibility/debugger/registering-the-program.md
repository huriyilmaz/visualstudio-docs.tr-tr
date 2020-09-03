---
title: Program kaydediliyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b68fa67f784d155288482ad724b632ed5ba5fa41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713167"
---
# <a name="register-the-program"></a>Programı Kaydet
Hata ayıklama altyapısı bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilen bir bağlantı noktasını aldıktan sonra, bir programın hata ayıklamasını etkinleştirmeye yönelik bir sonraki adım, bağlantı noktası ile kaydettirilmelidir. Kaydolduktan sonra, program hata ayıklama için aşağıdaki yollardan biriyle kullanılabilir:

- Hata ayıklayıcının çalışan bir uygulamanın hata ayıklama denetimini ele geçirmesine olanak sağlayan ekleme işlemi.

- Just-In-Time (JıT) hata ayıklayıcı, bir hata ayıklayıcının bağımsız olarak çalışan bir programın olay ayıklamasına olanak tanır. Çalışma zamanı mimarisi bir hata yakalarsa, işletim sistemi veya çalışma zamanı ortamı, hatalı programın bellek ve kaynaklarını serbest bırakmadan önce hata ayıklayıcıya bildirilir.

## <a name="registering-procedure"></a>Yordam kaydediliyor

### <a name="to-register-your-program"></a>Programınızı kaydetmek için

1. Bağlantı noktası tarafından uygulanan [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) yöntemini çağırın.

     `IDebugPortNotify2::AddProgramNode`[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimine yönelik bir işaretçi gerektirir.

     Genellikle, işletim sistemi veya çalışma zamanı ortamı bir program yüklediğinde program düğümünü oluşturur. Hata ayıklama altyapısının (DE) programı yüklemesi istenirse, DE program düğümünü oluşturur ve kaydeder.

     Aşağıdaki örnekte, programı başlatan hata ayıklama altyapısı gösterilmektedir ve bir bağlantı noktasıyla kayıt yapılır.

    > [!NOTE]
    > Bu kod örneği, bir işlemi başlatmak ve sürdürmenin tek yolu değildir; Bu kod, genellikle bir programı bağlantı noktasıyla kaydetme örneğidir.

    ```cpp
    // This is an IDebugEngineLaunch2 method.
    HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                          IDebugPort2 *pPort,
                                          /* omitted parameters */,
                                          IDebugProcess2**ppDebugProcess)
    {
        // do stuff here to set up for a launch (such as handling the other parameters)
        ...

        // Now get the IPortNotify2 interface so we can register a program node
        // in CDebugEngine::ResumeProcess.
        CComPtr<IDebugDefaultPort2> spDefaultPort;
        HRESULT hr = pPort->QueryInterface(&spDefaultPort);
        if (SUCCEEDED(hr))
        {
            CComPtr<IDebugPortNotify2> spPortNotify;
            hr = spDefaultPort->GetPortNotify(&spPortNotify);
            if (SUCCEEDED(hr))
            {
                // Remember the port notify so we can use it in ResumeProcess.
                m_spPortNotify = spPortNotify;

                // Now launch the process in a suspended state and return the
                // IDebugProcess2 interface
                CComPtr<IDebugPortEx2> spPortEx;
                hr = pPort->QueryInterface(&spPortEx);
                if (SUCCEEDED(hr))
                {
                    // pass on the parameters we were given (omitted here)
                    hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
                }
            }
        }
        return(hr);
    }

    HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
    {
        // Make a program node for this process
        HRESULT hr;
        CComPtr<IDebugProgramNode2> spProgramNode;
        hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
        if (SUCCEEDED(hr))
        {
            hr = m_spPortNotify->AddProgramNode(spProgramNode);
            if (SUCCEEDED(hr))
            {
                // resume execution of the process using the port given to us earlier.
               // (Querying for the IDebugPortEx2 interface is valid here since
               // that's how we got the IDebugPortNotify2 interface in the first place.)
                CComPtr<IDebugPortEx2> spPortEx;
                hr = m_spPortNotify->QueryInterface(&spPortEx);
                if (SUCCEEDED(hr))
                {
                    hr  = spPortEx->ResumeProcess(pDebugProcess);
                }
            }
        }
        return(hr);
    }

    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktası alma](../../extensibility/debugger/getting-a-port.md)
- [Bir programın ayıklanamayacağını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
