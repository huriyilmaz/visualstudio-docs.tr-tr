---
title: Bağlantı Noktası | Microsoft Docs
description: Program Visual Studio bağlantı noktasına kaydetmek ve işlem bilgileri isteklerini karşılamak için hata ayıklama altyapısına nasıl bağlantı noktası sağlar?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 028f52d6fe688802f4d5fa030b0661f25d5e98fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057908"
---
# <a name="get-a-port"></a>Bağlantı noktası al
Bağlantı noktası, işlemlerin üzerinde çalıştırıldıkları makineye yapılan bağlantıyı temsil eder. Bu makine yerel makine veya uzak makine olabilir (büyük olasılıkla Windows tabanlı olmayan bir işletim sistemi çalıştırıyor olabilir; daha fazla bilgi için [bkz.](../../extensibility/debugger/ports.md) Bağlantı noktaları).

Bağlantı noktası, [IDebugPort2 arabirimiyle temsil](../../extensibility/debugger/reference/idebugport2.md) edilen bir bağlantı noktasıdır. Bağlantı noktasının bağlı olduğu makinede çalışan işlemler hakkında bilgi almak için kullanılır.

Hata ayıklama altyapısının program düğümlerini bağlantı noktasına kaydetmek ve işlem bilgilerine ilişkin istekleri karşılamak için bir bağlantı noktasına erişmesi gerekir. Örneğin, hata ayıklama altyapısı [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimini uygulayıyorsa, [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) yönteminin uygulaması, gerekli işlem bilgileri döndürül için bağlantı noktasını sorabilir.

Visual Studio hata ayıklama altyapısına gerekli bağlantı noktasını sağlar ve bu bağlantı noktasını bir bağlantı noktası sağlayıcıdan ediner. Bir program (hata ayıklayıcısının içinde veya Tam Zamanında [JIT] iletişim kutusunu tetikleyen bir özel durum nedeniyle) ekli ise, kullanıcıya kullanmak üzere taşıma seçeneği (bağlantı noktası sağlayıcı için başka bir ad) verilir. Aksi takdirde, kullanıcı programı hata ayıklayıcısından başlatıyorsa proje sistemi, kullanmak üzere bağlantı noktası sağlayıcıyı belirtir. Her iki durumda da Visual Studio bir [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimiyle temsil edilen bağlantı noktası tedarikçinin örneğini ve bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) arabirimiyle [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) çağırarak yeni bir bağlantı noktası sorar. Bu bağlantı noktası daha sonra hata ayıklama altyapısına bir formda veya başka bir formda geçirebilirsiniz.

## <a name="example"></a>Örnek
Bu kod parçası, ResumeProcess'te bir program düğümünü kaydetmek için [LaunchSuspended'e](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) sağlanan bağlantı noktasının [nasıl kullanılır?](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) Bu kavramla doğrudan ilgili olan parametreler netlik sağlamak için atlanmıştır.

> [!NOTE]
> Bu örnek, işlemi başlatmak ve sürdürmek için bağlantı noktasını kullanır ve bağlantı noktası üzerinde [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) arabiriminin uygulandığını varsayıyor. Bu hiçbir şekilde bu görevleri gerçekleştirmenin tek yolu değildir ve bağlantı noktası, programın [IDebugProgramNode2'nin](../../extensibility/debugger/reference/idebugprogramnode2.md) verilmesi dışında da dahil bile olabilir.

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
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Programı kaydetme](../../extensibility/debugger/registering-the-program.md)
- [Bir programın hata ayıklamasını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Bağlantı noktası sağlayıcıları](../../extensibility/debugger/port-suppliers.md)
- [Bağlantı noktaları](../../extensibility/debugger/ports.md)
