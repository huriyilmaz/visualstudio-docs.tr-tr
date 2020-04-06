---
title: Programa Kayıt | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713167"
---
# <a name="register-the-program"></a>Programı kaydedin
Hata ayıklama altyapısı bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilen bir bağlantı noktası satın aldıktan sonra, programın hata ayıklanmasına olanak sağlamanın bir sonraki adımı, bağlantı noktasına kaydetmektir. Kayıt olduktan sonra, program aşağıdaki araçlardan biri ile hata ayıklama için kullanılabilir:

- Hata ayıklamanın çalışan bir uygulamanın tam hata ayıklama denetimini kazanmasını sağlayan ekleme işlemi.

- Tam zamanında (JIT) hata ayıklama, bir hata ayıklama bağımsız çalışan bir programın sonra-the-fact hata ayıklama sağlar. Çalışma zamanı mimarisi bir hata yakaladığında, hata ayıklayıcı işletim sistemi veya çalışma zamanı ortamı hata programının bellek ve kaynaklarını serbest bırakmadan önce bildirilir.

## <a name="registering-procedure"></a>Kayıt prosedürü

### <a name="to-register-your-program"></a>Programınızı kaydetmek için

1. Bağlantı noktası tarafından uygulanan [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) yöntemini arayın.

     `IDebugPortNotify2::AddProgramNode`[iDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi için bir işaretçi gerektirir.

     Genellikle, işletim sistemi veya çalışma zamanı ortamı bir program yükler, program düğümü oluşturur. Hata ayıklama motorundan (DE) programı yüklemesi istenirse, DE program düğümini oluşturur ve kaydeder.

     Aşağıdaki örnek, hata ayıklama altyapısının programı başlattığını ve bir bağlantı noktasına kaydettiğini gösterir.

    > [!NOTE]
    > Bu kod örneği, bir işlemi başlatmanın ve devam ettirmenin tek yolu değildir; bu kod esas olarak bir bağlantı noktası ile bir program kayıt bir örnektir.

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
- [Bir programın debutlanmasına olanak sağlama](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
