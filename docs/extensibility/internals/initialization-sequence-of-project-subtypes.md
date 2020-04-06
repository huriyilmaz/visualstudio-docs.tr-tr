---
title: Proje Alt Türlerinin Başlatma Sırası | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707627"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Proje Alt Türlerinin Başlatılma Sırası
Çevre temel proje fabrika uygulaması çağırarak bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>proje inşa eder. Proje alt türünün yapısı, ortam, proje dosyasının uzantısı için proje türü GUID listesinin boş olmadığını belirlediğinde başlar. Proje dosyası uzantısı ve project GUID, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projenin [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] bir veya proje türü olup olmadığını belirtir. Örneğin, .vbproj uzantısı ve {F184B08F-C81C-45F6-A57F-5ABD9991F28F} [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir proje tanımlar.

## <a name="environments-initialization-of-project-subtypes"></a>Çevrenin Proje Alt Türlerinin Başlatılması
 Aşağıdaki yordam, birden çok proje alt türü tarafından toplanan bir proje sisteminin başlatma sırasını ayrıntılarıyla anlatır.

1. Ortam temel projenin çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>ve proje proje dosyasını parsese ederken, toplam proje türü GUIDs listesi olmadığını `null`keşfeder. Proje, projesini oluşturmayı doğrudan durdurulur.

2. Proje, `QueryService` yöntemin ortamının uygulanmasını <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> kullanarak bir proje alt türü oluşturmak için hizmet çağırır. Bu yöntem de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> en dıştaki proje alt türünden <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> başlayarak proje türü GUID'lerin listesini yürürken uygulamalarınız ve yöntemleriniz için özyinelemeli işlev çağrıları yapar.

     Aşağıdaki başlatma adımlarını ayrıntılarıyla anlatır.

    1. Yöntemin <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> çevrenin uygulanması aşağıdaki `HrCreateInnerProj` işlev bildirimi ile yöntemi çağırır:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Bu işlev ilk kez çağrıldığında, yani en dıştaki proje alt `pOuter` `pOwner` türü için `null` parametreler ve olarak geçirilir ve `IUnknown` `pOuter`işlev en dıştaki proje alt türünü ayarlar.

    2. Sonraki ortamda `HrCreateInnerProj` listede ikinci proje türü GUID ile işlevi çağırır. Bu GUID, toplama dizisinde temel projeye doğru adım atan ikinci iç proje alt türüne karşılık gelir.

    3. Şimdi `pOuter` en dıştaki `IUnknown` proje alt türüne işaret `HrCreateInnerProj` ediyor ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> uygulamanızı takip eden <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>bir çağrıyı takip eden uygulamanızı çağırıyor. Yöntemde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> en dıştaki `IUnknown` proje alt tipinin `pOuter`kontrolünden geçersiniz. Sahip olunan projenin (iç proje alt türü) burada toplam proje nesnesini oluşturması gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> Yöntem uygulamasında, biraraya `IUnknown` gelmekte olan iç projenin işaretçisi geçersiniz. Bu iki yöntem toplama nesnesini oluşturur ve uygulamalarınızın, proje alt türünün kendisine bir başvuru sayısı tutmadığından emin olmak için COM toplama kurallarına uyması gerekir.

    4. `HrCreateInnerProj`uygulamanızı <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>çağırır. Bu yöntemde, proje alt türü başlatma işini yapar. Örneğin, çözüm olaylarını <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5. `HrCreateInnerProj`listedeki son GUID (temel proje) erişilene kadar özyinelemeli olarak adlandırılır. Bu çağrıların her biri için c'den d'ye kadar olan adımlar yinelenir. `pOuter`her toplama düzeyi için `IUnknown` en dıştaki proje alt türüne işaret edin.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, programlı süreç, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntemin çevre tarafından uygulandığı gibi yaklaşık bir gösteriminde ayrıntılı olarak açıklanır. Kod sadece bir örnektir; derlenecek şekilde tasarlanmamıştır ve tüm hata denetimi netlik için kaldırıldı.

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
