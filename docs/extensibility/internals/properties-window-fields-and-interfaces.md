---
title: Özellikler Pencere Alanları ve Arayüzler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706160"
---
# <a name="properties-window-fields-and-interfaces"></a>Özellikler Penceresi Alanları ve Arabirimleri
**Özellikler** penceresinde hangi bilgilerin görüntüleneceğini belirlemek için seçim modeli, IDE'de odağı olan pencereyi temel adamıştır. Seçili penceredeki her pencere ve nesne, seçim bağlamı nesnesinin genel seçim bağlamına itilmiş olmasını sağlayabilir. Ortam, bu pencere odağı olduğunda, genel seçim bağlamını pencere çerçevesindeki değerlerle güncelleştirir. Odak değiştiğinde, seçim bağlamı da değişir.

## <a name="tracking-selection-in-the-ide"></a>IDE'de İzleme Seçimi
 IDE'ye ait pencere çerçevesi veya sitenin <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>adı . Aşağıdaki adımlar, kullanıcının odağı başka bir açık pencereye değiştirmesi veya **Çözüm Gezgini'nde**farklı bir proje öğesi seçmesi nedeniyle bir seçimdeki değişikliğin **Özellikler** penceresinde görüntülenen içeriği değiştirmek için nasıl uygulandığını gösterir.

1. Seçilen pencerede sited VSPackage tarafından oluşturulan nesne <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> çağırmak <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>için çağırır.

2. Seçili pencere tarafından sağlanan seçim kapsayıcısı, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> kendi nesnesini oluşturur. Seçim değiştiğinde, VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> **Özellikler** penceresi de dahil olmak üzere ortamdaki tüm dinleyicileri değişikliği bildirmeyi çağırır. Ayrıca hiyerarşiye ve yeni seçimle ilgili madde bilgilerine erişim sağlar.

3. Parametredeki seçili hiyerarşi <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> öğelerini `VSHPROPID_BrowseObject` çağırmak ve <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> geçmek nesneyi dolduruyor.

4. [IDispatch Arabirimi'nden](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) türetilen bir nesne __VSHPROPID için [döndürülür. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) istenen öğe için ve ortam onu bir <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> öğeye sarar (aşağıdaki adıma bakın). Arama başarısız olursa, ortam seçim kapsayıcısı __VSHPROPID geçmek için `IVsHierarchy::GetProperty`ikinci bir arama [yapar. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>)hiyerarşi öğesinin veya maddelerin tedarik ineVSHPROPID_SelContainer.

    Projeniz VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> bunu uygulayan ortam tarafından sağlanan pencere VSPackage (örneğin, **Solution Explorer)** adına oluşturduğundan <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oluşturmaz.

5. Ortam, Özellikler penceresini <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> doldurmak için `IDispatch` arabirime dayalı nesneleri **Properties** almak için yöntemleri çağırır.

   **Özellikler** penceresindeki bir değer değiştirildiğinde, `IVsTrackSelectionEx::OnElementValueChangeEx` VSPackages uygular ve `IVsTrackSelectionEx::OnSelectionChangeEx` değişikliği öğe değerine bildirir. Ortam daha sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> çağırır veya **özellikler** penceresinde görüntülenen bilgileri özellik değerleri ile senkronize tutmak için. Daha fazla bilgi için, [Özellikler Penceresinde Özellik Değerlerini Güncelleştirme'ye](#updating-property-values-in-the-properties-window)bakın.

   Bu öğeyle ilgili özellikleri görüntülemek için **Solution Explorer'da** farklı bir proje öğesi seçmenin yanı sıra, **Özellikler** penceresinde bulunan açılır listeyi kullanarak form veya belge penceresinden farklı bir nesne de seçebilirsiniz. Daha fazla bilgi için [Bkz. Özellikler Penceresi Nesne Listesi.](../../extensibility/internals/properties-window-object-list.md)

   **Özellikler** penceresinde ki bilgilerin alfabetikten kategorik olarak görüntülenme biçimini değiştirebilir ve varsa **Özellikler** penceresindeki uygun düğmeleri tıklatarak seçili bir nesne için özellik sayfası da açabilirsiniz. Daha fazla bilgi için [Bkz. Özellikler Pencere Düğmeleri](../../extensibility/internals/properties-window-buttons.md) ve [Özellik Sayfaları.](../../extensibility/internals/property-pages.md)

   Son olarak, **Özellikler** penceresinin alt kısmında da **Özellikler** penceresi ızgarasında seçilen alanın bir açıklamasını içerir. Daha fazla bilgi için, [Özellikler Penceresinden Alan Açıklamalarını Alma'ya](#getting-field-descriptions-from-the-properties-window)bakın.

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Özellikler Penceresindeözellik Değerlerini Güncelleştirme
**Özellikler** penceresini özellik değeri değişiklikleriyle eşit tutmanın iki yolu vardır. Bunlardan ilki, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ortam tarafından sağlanan araç ve belge pencerelerine erişim ve bunların oluşturulması da dahil olmak üzere temel pencereleme işlevlerine erişim sağlayan arabirimi aramaktır. Aşağıdaki adımlar bu eşitleme işlemini açıklar.

### <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell kullanarak özellik değerlerini güncelleme

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell arabirimini kullanarak özellik değerlerini güncelleştirmek için

1. VSPackages' <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> in, projelerin veya düzenleyicilerin araç veya belge pencereleri oluşturması veya kaydetmesi gerektiğinde (hizmet yoluyla) arayın. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>

2. Özellikler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> **penceresini,** olayları uygulamadan ve ateşlemeden <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> bir proje (veya **Özellikler** penceresi tarafından gezinen diğer seçili nesne) için özellik değişiklikleriyle eşit tutmak için uygulayın.

3. Yöntemleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> ve hiyerarşiuygulamak için gerek kalmadan hiyerarşi olayları istemci bildirimi kurmak ve <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>devre dışı, sırasıyla.

### <a name="updating-property-values-using-iconnection"></a>IConnection kullanarak Özellik Değerlerini Güncelleştirme
 **Özellikler** penceresini özellik değeri değişiklikleriyle eşit tutmanın `IConnection` ikinci yolu, giden arabirimlerin varlığını belirtmek için bağlanabilir nesneüzerinde uygulamaktır. Özellik adını yerelleştirmek istiyorsanız, nesnenizi .'den <xref:System.ComponentModel.ICustomTypeDescriptor>türetin Uygulama, <xref:System.ComponentModel.ICustomTypeDescriptor> döndürdeceği özellik tanımlayıcılarını değiştirebilir ve bir özelliğin adını değiştirebilir. Açıklamayı yerelleştirmek için, Açıklama özelliğinden <xref:System.ComponentModel.DescriptionAttribute> türetilen ve geçersiz kılınan bir öznitelik oluşturun.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection arabiriminin uygulanmasında dikkat edilmesi gerekenler

1. `IConnection`<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> arabirimi olan bir sayısalalt nesneye erişim sağlar. Ayrıca, her biri <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> arabirimi uygulayan tüm bağlantı noktası alt nesnelerine erişim sağlar.

2. Herhangi bir gözatma nesnesi <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> bir olayı uygulamaktan sorumludur. **Özellikler** penceresi, `IConnection`'den geçen olay için tavsiyelerde bulunacaktır.

3. Bir bağlantı noktası, uygulanmasında kaç bağlantıya (bir veya <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>daha fazla) izin verdiğini denetler. Yöntemden yalnızca bir arabirim <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> in returnatmasına izin veren bir bağlantı noktası. <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>

4. İstemci `IConnection` <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> arabirimi olan bir yerumerator alt nesneye erişmek için arabirimi arayabilir. Arabirim <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> daha sonra her giden arabirim kimliği (IID) için bağlantı noktaları sayısallandırmak için çağrılabilir.

5. `IConnection`giden her IID için <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> arabirim ile bağlantı noktası alt nesnelere erişim elde etmek için de çağrılabilir. <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Arabirim aracılığıyla, istemci bağlanabilir nesne ve istemcinin kendi eşitlemeile bir danışma döngüsü başlatır veya sonlandırır. İstemci ayrıca, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> bildiği bağlantıları sayısallandırmak için <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> arabirime arabirimi olan bir sayısal nesne elde etmek için arabirimi de arayabilir.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Özellikler Penceresinden Alan Açıklamaları Alma
**Özellikler** penceresinin alt kısmında, açıklama alanı seçili özellik alanıyla ilgili bilgileri görüntüler. Bu özellik varsayılan olarak açık. Açıklama alanını gizlemek istiyorsanız, **Özellikler** penceresini sağ tıklatın ve **Açıklama'yı**tıklatın. Bunu yapmak, menü penceresindeaçıklama **başlığının** yanındaki onay işaretini de kaldırır. **Açıklama'yı** yeniden kaydırmak için aynı adımları izleyerek alanı yeniden görüntüleyebilirsiniz.

 Açıklama alanındaki bilgiler <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Her yöntem, arabirim, coclass ve benzeri tür `helpstring` kitaplığında yerelleştirilmemiş bir öznitelik olabilir. **Özellikler** penceresi dizeyi <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.

### <a name="to-specify-localized-help-strings"></a>Yerelleştirilmiş yardım dizelerini belirtmek için

1. Tür `helpstringdll` kitaplığındaki kitaplık deyimine öznitelik ekleyin (`typelib`).

   > [!NOTE]
   > Tür kitaplığı bir nesne kitaplığı (.olb) dosyasındaysa, bu adım isteğe bağlıdır.

2. Dizeleri için öznitelikleri belirtin. `helpstringcontext` Öznitelikleri de `helpstring` belirtebilirsiniz.

    Bu öznitelikler, `helpfile` gerçek `helpcontext` .chm dosyası Yardım konularında bulunan özniteliklerden farklıdır.

   Vurgulanan özellik adı için görüntülenecek açıklama bilgilerini almak için, **Özellikler** penceresi, çıktı dizesi için istenen <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> `lcid` özniteliği belirterek seçilen özelliği çağırır. Dahili <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> olarak, öznitelikte belirtilen `helpstringdll` .dll `DLLGetDocumentation` dosyasını bulur ve belirtilen bağlam `lcid` ve öznitelik ile bu .dll dosyasını çağırır.

   İmza ve uygulama `DLLGetDocumentation` şunlardır:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 İşlev, `DLLGetDocumentation` DLL için .def dosyasında tanımlanan bir dışa aktarma olmalıdır.

 Dahili olarak, bir .olb dosyası aslında bir DLL olan oluşturulur. Bu DLL bir kaynak, tür kitaplığı (.tlb) dosyası `DLLGetDocumentation`ve bir dışa aktarılan işlev içerir.

 .olb dosyaları söz konusu `helpstringdll` olduğunda, .tlb dosyasının kendisini içeren aynı dosya olduğu için öznitelik isteğe bağlıdır.

 Dizelerin **Açıklamalar** bölmesinde gösterilmesini sağlamak için, bu nedenle yapmanız gereken `helpstring` en az şey tür kitaplığındaki özniteliği belirtmektir. Bu dizelerin yerelleştirilmesini istiyorsanız, `helpstringdll` (isteğe bağlı) özniteliği `helpstringcontext` ve (gerekli) özniteliği belirtmeniz ve uygulamanız `DLLGetDocumentation`gerekir.

 IDL'nin `helpstringcontext` özniteliği üzerinden yerelleştirilmiş bilgi alırken uygulanması gereken ek arabirim `DLLGetDocumentation`yoktur.

 Yerelleştirilmiş adı ve bir özelliğin açıklamasını elde etmenin <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>başka bir yolu da uygulamaktır. Bu yöntemin uygulanmasıyla ilgili daha fazla bilgi için [Özellikler Pencere Alanları ve Arabirimleri'ne](../../extensibility/internals/properties-window-fields-and-interfaces.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
