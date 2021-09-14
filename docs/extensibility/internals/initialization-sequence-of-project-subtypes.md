---
title: Project Alt Türleri Başlatma | Microsoft Docs
description: Birden çok proje alt türü tarafından toplanan bir Visual Studio için bir proje ortamında başlatma dizisi hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2a7458d2529511362b832a85819d758c26dc3cdf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725054"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Proje Alt Türlerinin Başlatılma Sırası
Ortam, temel proje fabrikası uygulamasını çağırarak bir proje yapısına <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> sahiptir. Ortam, proje dosyasının uzantısı için proje türü GUID listesinin boş olmadığını belirlerken bir proje alt türünün yapısı başlar. Proje dosyası uzantısı ve proje GUID'si, projenin bir veya proje [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] türü [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] olup olmadığını belirtir. Örneğin, .vbproj uzantısı ve {F184B08F-C81C-45F6-A57F-5ABD9991F28F} bir projeyi [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tanımladı.

## <a name="environments-initialization-of-project-subtypes"></a>Ortamın Project Başlatması
 Aşağıdaki yordam, birden çok proje alt türü tarafından toplanan bir proje sisteminin başlatma sırasını ayrıntılarıyla gösterir.

1. Ortam, temel projenin ' ini çağırır ve proje proje dosyasını ayrıştırırken toplam proje türü GUID'ler <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> listesinin olmadığını fark `null` eder. Proje, doğrudan projesini oluşturmayı sonlandırıyor.

2. Proje, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> yönteminin ortamın uygulamasını kullanarak bir proje alt türü oluşturmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> hizmetine çağrılar. Bu yöntemde ortam, en dıştaki proje alt türüyle başlayarak proje türü GUID'ler listesinden ilerlerken , ve metotları uygulamanıza özyinelemeli <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> işlev çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> yapar.

     Aşağıda başlatma adımları ayrıntılı olarak ve ayrıntılı olarak ve ayrıntılı olarak ve ayrıntılı bir şekilde ve ayrıntılı olarak ve ayrıntılı bir şekilde ve ayrıntılı bir şekilde

    1. Ortamın yöntemi uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> aşağıdaki işlev `HrCreateInnerProj` bildirimiyle yöntemini çağırmaktadır:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Bu işlev ilk kez çağrıldı mı, yani en dıştaki proje alt türü için ve parametreleri olarak geçirildi ve işlevi en dıştaki proje alt türü olarak `pOuter` `pOwner` `null` `IUnknown` `pOuter` ayarlar.

    2. Ardından ortam, `HrCreateInnerProj` listede ikinci proje türü GUID olan işlevi çağırmaktadır. Bu GUID, toplama dizisinde temel projeye doğru adımlamanın ikinci iç proje alt türüne karşılık geliyor.

    3. artık en dıştaki proje alt türüne işaret ediyor ve uygulamasını ve ardından uygulamanıza `pOuter` `IUnknown` yönelik bir `HrCreateInnerProj` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> çağrıyı <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> çağırıyor. yönteminde <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> en dıştaki `IUnknown` proje alt türü olan denetimine geçersiniz. `pOuter` Sahip olunan projenin (iç proje alt türü) burada toplam proje nesnesini oluşturması gerekir. Yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> uygulamasında, toplanmış olan iç projenin `IUnknown` işaretçisini iletirsiniz. Bu iki yöntem toplama nesnesini oluşturur ve bir proje alt türün kendisine bir başvuru sayısı tutmaması için uygulamalarınızı COM toplama kurallarına uyması gerekir.

    4. `HrCreateInnerProj` , uygulamasını çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> bir uygulamadır. Bu yöntemde, proje alt türü başlatma çalışmalarını yapar. Örneğin, çözüm olaylarını 'a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> kaydedesiniz.

    5. `HrCreateInnerProj` , listede son GUID'e (temel proje) ulaşıncaya kadar tekrar tekrar çağrılır. Bu çağrıların her biri için c ile d arasında adımlar yinelenir. `pOuter` her toplama düzeyi için en `IUnknown` dıştaki proje alt türüne işaret ediyor.

## <a name="example"></a>Örnek

Aşağıdaki örnek, ortam tarafından uygulanan yöntemin yaklaşık <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> gösteriminde programlı işlemi ayrıntılı olarak açıklar. Kod yalnızca bir örnektir; derlenmiş olması amaçlanmaz ve tüm hata denetimi netlik sağlamak için kaldırılmıştır.

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
