---
title: Bağlantı noktası alma | Microsoft Docs
description: Visual Studio 'Nun program düğümlerini bağlantı noktası ile kaydetmek ve işlem bilgileri isteklerini karşılamak için hata ayıklama altyapısına bir bağlantı noktası sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f3ee9c145a4c6275f64d357d87ac1cc284bfac6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921291"
---
# <a name="get-a-port"></a>Bağlantı noktası al
Bir bağlantı noktası, işlemlerin çalıştığı bir makineye bağlantıyı temsil eder. Bu makine, yerel makine veya uzak bir makine olabilir (Windows tabanlı olmayan bir işletim sistemi çalışıyor olabilir; daha fazla bilgi için bkz. [bağlantı noktaları](../../extensibility/debugger/ports.md) ).

Bir bağlantı noktası [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilir. Bağlantı noktasının bağlandığı makinede çalışan süreçler hakkında bilgi almak için kullanılır.

Bir hata ayıklama altyapısının, program düğümlerini bağlantı noktasıyla kaydetmek ve işlem bilgileri isteklerini karşılamak için bir bağlantı noktasına erişmesi gerekir. Örneğin, hata ayıklama altyapısı [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimini uyguluyorsa, [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) yönteminin uygulanması, bağlantı noktasında gerekli işlem bilgilerinin döndürülmesini isteyebilir.

Visual Studio, hata ayıklama altyapısına gerekli bağlantı noktasını sağlar ve bu bağlantı noktasını bir bağlantı noktası tedarikçiden alır. Bir program, (hata ayıklayıcı içinden veya tam zamanında [JıT] iletişim kutusunu tetikleyen bir özel durum nedeniyle) bağlıysa, kullanıcıya kullanmak üzere taşıma seçimi (bir bağlantı noktası sağlayıcısı için başka bir ad) verilir. Aksi takdirde, Kullanıcı programı hata ayıklayıcı içinden başlattığında, proje sistemi kullanılacak bağlantı noktası tedarikçisini belirtir. Her iki durumda da, Visual Studio bir [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimiyle temsil edilen bağlantı noktası Tedarikçini başlatır ve bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) arabirimiyle [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) çağırarak yeni bir bağlantı noktası ister. Bu bağlantı noktası daha sonra hata ayıklama motoruna bir biçimde veya başka bir biçimde geçirilir.

## <a name="example"></a>Örnek
Bu kod parçası, bir program düğümünü [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)'e kaydetmek üzere [launchaskıya alındı](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) için sağlanan bağlantı noktasının nasıl kullanılacağını gösterir. Bu kavram ile doğrudan ilgili olmayan parametreler açıklık için atlandı.

> [!NOTE]
> Bu örnek, bağlantı noktasını kullanarak işlemi başlatabilir ve sürdürülür ve [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) arabiriminin bağlantı noktasında uygulandığını varsayar. Bu, bu görevleri gerçekleştirmenin tek yolu değildir ve bu nedenle, programın kendisine verilen [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) sahip olması dışında bile bağlantı noktasının başka bir şekilde dahil olmaması olasıdır.

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
- [Program kaydediliyor](../../extensibility/debugger/registering-the-program.md)
- [Bir programın ayıklanamayacağını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Bağlantı noktası tedarikçileri](../../extensibility/debugger/port-suppliers.md)
- [Bağlantı noktaları](../../extensibility/debugger/ports.md)
