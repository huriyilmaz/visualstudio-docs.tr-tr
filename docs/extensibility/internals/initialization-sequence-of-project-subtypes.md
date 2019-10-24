---
title: Proje alt türleri başlatma dizisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 678f704c73a39cdf2130d36fcfb1a74925dd89d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726870"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Proje Alt Türlerinin Başlatılma Sırası
Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> temel proje fabrikası uygulamasını çağırarak bir proje oluşturur. Bir proje alt türünün oluşturulması, ortam bir proje dosyası uzantısının proje türü GUID listesinin boş olmadığını belirlediğinde başlar. Proje dosyası uzantısı ve proje GUID 'SI projenin bir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] mı yoksa [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proje türü mi olduğunu belirtir. Örneğin,. vbproj uzantısı ve {F184B08F-C81C-45F6-A57F-5ABD9991F28F} [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir proje belirler.

## <a name="environments-initialization-of-project-subtypes"></a>Ortamın proje alt türlerini başlatması
 Aşağıdaki yordamda birden fazla proje alt türleri tarafından toplanan bir proje sisteminin başlatma sırası ayrıntılı olarak verilmiştir.

1. Ortam, temel projenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> çağırır ve proje proje dosyasını ayrıştırdığında, toplama proje türü GUID listesinin `null` değil olduğunu bulur. Proje doğrudan projesini oluşturmaya devam eder.

2. Proje, <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> hizmetinde, ortamın <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yönteminin uygulamasını kullanarak bir proje alt türü oluşturmak için `QueryService` çağırır. Bu yöntemde, ortam, en dıştaki proje alt türüyle başlayarak proje türü GUID 'Leri listesini yürüyerek <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> yöntemleri için özyinelemeli işlev çağrıları yapar.

     Aşağıda, başlatma adımları ayrıntılı olarak verilmiştir.

    1. Ortamın <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yönteminin uygulanması, aşağıdaki işlev bildirimiyle `HrCreateInnerProj` yöntemini çağırır:

         \<CodeContentPlaceHolder > 0 </CodeContentPlaceHolder>

         Bu işlev ilk kez çağrıldığında, yani en dıştaki proje alt türü için, `pOuter` ve `pOwner` parametreleri `null` olarak geçirilir ve işlevi en dıştaki proje alt türünü `pOuter` `IUnknown` olarak ayarlar.

    2. Daha sonra ortam, listede ikinci proje türü GUID 'ı ile `HrCreateInnerProj` işlevini çağırır. Bu GUID, ikinci iç proje alt türüne karşılık gelen toplama dizisindeki temel projeye doğru adımlanıyor.

    3. @No__t_0 artık en dıştaki proje alt türünün `IUnknown` işaret eder ve `HrCreateInnerProj` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> uygulamanızı ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> uygulamanıza çağrı yaparak çağırır. @No__t_0 Yöntem ' de en dıştaki proje alt türünün denetim `IUnknown` `pOuter`. Sahip olunan projenin (iç proje alt türü), burada toplam proje nesnesini oluşturması gerekir. @No__t_0 yöntemi uygulamasında, toplanmakta olan iç projenin `IUnknown` bir işaretçiye geçiş yapabilirsiniz. Bu iki yöntem toplama nesnesini oluşturur ve uygulamanız bir proje alt türünün kendine başvuru sayısı tutmaya bitmesini sağlamak için COM toplama kurallarını izlemesi gerekir.

    4. `HrCreateInnerProj` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> uygulamanızı çağırır. Bu yöntemde, proje alt türü başlatma işi yapar. Örneğin, çözüm olaylarını <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> kaydedebilirsiniz.

    5. `HrCreateInnerProj`, listedeki son GUID (temel proje) öğesine ulaşılana kadar yinelemeli olarak çağırılır. Bu çağrıların her biri için, c ile d arasındaki adımlar yinelenir. `pOuter` her toplama düzeyi için `IUnknown` en dıştaki proje alt türüne işaret eder.

## <a name="example"></a>Örnek

Aşağıdaki örnek, ortam tarafından uygulandığı şekliyle <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yönteminin yaklaşık bir gösteriminde programlı işlem ayrıntılarını ayrıntılardır. Kod yalnızca bir örnektir; derlenmesi amaçlanmamıştır ve tüm hata denetimi açıklık için kaldırılmıştır.

```cpp
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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)