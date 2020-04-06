---
title: Liman Alma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738637"
---
# <a name="get-a-port"></a>Bir bağlantı noktası alın
Bağlantı noktası, işlemlerin çalıştırıldığı bir makineye olan bağlantıyı temsil eder. Bu makine yerel makine veya uzak bir makine olabilir (windows tabanlı olmayan bir işletim sistemi çalışıyor olabilir; daha fazla bilgi için [Bağlantı Noktaları'na](../../extensibility/debugger/ports.md) bakın).

Bağlantı noktası [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilir. Bağlantı noktasının bağlı olduğu makinede çalışan işlemler hakkında bilgi edinmek için kullanılır.

Hata ayıklama altyapısının, program düğümlerini bağlantı noktasına kaydetmek ve işlem bilgileri isteklerini karşılamak için bir bağlantı noktasına erişmesi gerekir. Örneğin, hata ayıklama altyapısı [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimini uygularsa, [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) yönteminin uygulanması bağlantı noktasından gerekli işlem bilgilerinin döndürülülmesini isteyebilir.

Visual Studio hata ayıklama motoruna gerekli bağlantı noktasını sağlar ve bu bağlantı noktasını bir bağlantı noktası tedarikçisinden alır. Bir program ekli (hata ayıklayıcı nın içinden veya bir özel durum nedeniyle atılırsa, bu da Just-in-Time [JIT] iletişim kutusunu tetikler), kullanıcıya taşıma seçeneği (bağlantı noktası tedarikçisi için başka bir ad) verilir. Aksi takdirde, kullanıcı programı hata ayıklama nın içinden başlatıyorsa, proje sistemi kullanılacak bağlantı noktası tedarikçisini belirtir. Her iki durumda da Visual Studio, [iDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi yle temsil edilen bağlantı noktası tedarikçisini anında yönlendirir ve [AddPort'u](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) [iDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) arabirimiyle arayarak yeni bir bağlantı noktası ister. Bu bağlantı noktası daha sonra hata ayıklama motoruna şu veya bu şekilde aktarılır.

## <a name="example"></a>Örnek
Bu kod [parçası, ResumeProcess'de](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)bir program düğümü kaydetmek için [LaunchSuspended'e](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) verilen bağlantı noktasının nasıl kullanılacağını gösterir. Bu kavramla doğrudan ilişkili olmayan parametreler açıklık için atlanmıştır.

> [!NOTE]
> Bu örnek, işlemi başlatmak ve devam ettirmek için bağlantı noktasını kullanır ve bağlantı noktasında [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) arabiriminin uygulandığını varsayar. Bu hiçbir şekilde bu görevleri gerçekleştirmek için tek yoldur ve bağlantı noktası bile programın [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) verilen dışında dahil olmayabilir mümkündür.

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
- [Bir programın debutlanmasına olanak sağlama](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Liman tedarikçileri](../../extensibility/debugger/port-suppliers.md)
- [Bağlantı Noktaları](../../extensibility/debugger/ports.md)
