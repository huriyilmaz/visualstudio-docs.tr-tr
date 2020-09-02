---
title: Proje alt türleri başlatma dizisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5594d54c188c2f561dd66229e808e48068ba41a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192659"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Proje Alt Türlerinin Başlatılma Sırası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ortamı, öğesinin temel proje fabrikası uygulamasını çağırarak bir proje oluşturur <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . Bir proje alt türünün oluşturulması, ortam bir proje dosyası uzantısının proje türü GUID listesinin boş olmadığını belirlediğinde başlar. Proje dosyası uzantısı ve proje GUID 'SI projenin bir [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] veya proje türü olduğunu belirtir [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Örneğin,. vbproj uzantısı ve {F184B08F-C81C-45F6-A57F-5ABD9991F28F} bir [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projeyi belirler.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Ortamın proje alt türlerini başlatması  
 Aşağıdaki yordamda birden fazla proje alt türleri tarafından toplanan bir proje sisteminin başlatma sırası ayrıntılı olarak verilmiştir.  
  
1. Ortam, temel projenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> öğesini çağırır ve proje proje dosyasını ayrıştırdığında, toplama proje türü GUID listesinin değil olduğunu bulur `null` . Proje doğrudan projesini oluşturmaya devam eder.  
  
2. Proje, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> uygulamanın yöntemin uygulamasını kullanarak bir proje alt türü oluşturmak için hizmetini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> . Bu yöntemde, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> , en `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> dıştaki proje alt türüyle başlayan proje türü GUID 'leri listesini yürüyerek, ve uygulamalarına özyinelemeli işlev çağrıları yapar.  
  
    Aşağıda, başlatma adımları ayrıntılı olarak verilmiştir.  
  
   1. Ortamın <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntemi uygulamasının ' HrCreateInnerProj ' ' ' metodunu aşağıdaki işlev bildirimiyle çağırır:  
  
       ```  
       HRESULT HrCreateInnerProj  
       (  
           WCHAR *pwszGuids,  
           IUnknown *pOuter,  
           IVsAggregatableProject *pOwner,  
           LPCOLESTR pszFilename,  
           LPCOLESTR pszLocation,  
           LPCOLESTR pszName,  
           VSCREATEPROJFLAGS grfCreateFlags,  
           IUnknown **ppInner,  
           BOOL *pfCancelled  
       )  
       ```  
  
        Bu işlev ilk kez çağrıldığında, yani en dıştaki proje alt türü için parametreler `pOuter` ve `pOwner` olarak geçirilir `null` ve işlevi en dıştaki proje alt türünü olarak ayarlar `IUnknown` `pOuter` .  
  
   2. Daha sonra ortam, `HrCreateInnerProj` listede ikinci proje türü GUID 'i ile işlev çağırır. Bu GUID, ikinci iç proje alt türüne karşılık gelen toplama dizisindeki temel projeye doğru adımlanıyor.  
  
   3. `pOuter`Artık en `IUnknown` dıştaki proje alt türü ' ne işaret ediyor ve uygulamanıza yönelik `HrCreateInnerProj` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> bir çağrı tarafından ve uygulamanızı çağırıyor <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>Yöntemi içinde `IUnknown` , en dıştaki proje alt türünün denetlenmesini geçitirsiniz `pOuter` . Sahip olunan projenin (iç proje alt türü), burada toplam proje nesnesini oluşturması gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>Yöntem uygulamasında, `IUnknown` toplanmakta olan iç projenin bir işaretçisini geçitirsiniz. Bu iki yöntem toplama nesnesini oluşturur ve uygulamanız bir proje alt türünün kendine başvuru sayısı tutmaya bitmesini sağlamak için COM toplama kurallarını izlemesi gerekir.  
  
   4. `HrCreateInnerProj` Uygulamanızı çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . Bu yöntemde, proje alt türü başlatma işi yapar. Örneğin, çözüm olaylarını ' de kaydedebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .  
  
   5. `HrCreateInnerProj` , listedeki son GUID 'ye (temel proje) ulaşılana kadar yinelemeli olarak çağırılır. Bu çağrıların her biri için, c ile d arasındaki adımlar yinelenir. `pOuter` her toplama düzeyi için en dıştaki proje alt türüne işaret eder `IUnknown` .  
  
   Aşağıdaki örnek, ortam tarafından uygulandığı için yönteminin yaklaşık bir gösteriminde programlı işlem ayrıntılarını ayrıntılardır <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> . Kod yalnızca bir örnektir; derlenmek üzere tasarlanmamıştır ve tüm hata denetimi açıklık için kaldırılmıştır.  
  
## <a name="example"></a>Örnek  
  
### <a name="code"></a>Kod  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)
