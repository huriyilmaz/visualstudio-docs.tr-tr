---
title: Özellikler Pencere Alanları ve Arabirimler | Microsoft Docs
description: IDE'de odak noktası olan pencereye bağlı olarak Özellikler penceresi görüntülenen bilgileri belirleyen seçimi Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a74e82480d1a4c71179c0e0b0671bac4ae97191
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899634"
---
# <a name="properties-window-fields-and-interfaces"></a>Özellikler Penceresi Alanları ve Arabirimleri
Özellikler penceresinde hangi bilgilerin görüntülendiğinden  karar almak için yapılan seçim modeli, IDE'ye odaklanan pencereyi temel alan modeldir. Seçilen pencere içindeki her pencere ve nesne, seçim bağlamı nesnesinin genel seçim bağlamına itilmiş olması gerekir. Ortam, genel seçim bağlamını bir pencere çerçevesi odağına sahip olduğunda bir pencere çerçevesindeki değerlerle günceller. Odak değiştiğında seçim bağlamı da değişir.

## <a name="tracking-selection-in-the-ide"></a>IDE'de Seçimi İzleme
 IDE'nin sahip olduğu pencere çerçevesi veya sitenin adlı bir hizmeti <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> vardır. Aşağıdaki adımlar, kullanıcının odağı başka bir açık pencereye değiştirmesi veya **Çözüm Gezgini'de** farklı bir proje öğesi seçmesi nedeniyle bir seçimde yapılan değişikliğin Özellikler penceresinde görüntülenen içeriği değiştirmek için nasıl **uygulandığını** gösterir.

1. VSPackage'nız tarafından oluşturulan ve seçilen pencerede siteden çağrılan nesne çağrısı <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> yapmak için <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> çağrısında bulundu.

2. Seçilen pencere tarafından sağlanan seçim kapsayıcısı kendi nesnesini <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oluşturur. Seçim değişirse VSPackage, değişikliklerle ilgili Özellikler penceresi de dahil olmak üzere <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ortamdaki **dinleyicileri** bilgilendirmeye çağrır. Ayrıca, yeni seçimle ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.

3. çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ve parametresinde seçili hiyerarşi `VSHPROPID_BrowseObject` öğelerinin geçirmesi, nesneyi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> doldurmaktır.

4. [IDispatch Arabiriminden türetilen bir](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) nesne, [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) öğe için kullanılır ve ortam bunu bir içine sarmalar <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (aşağıdaki adıma bakın). Çağrı başarısız olursa, ortam ikinci bir çağrısı yapar ve bunu seçim `IVsHierarchy::GetProperty` kapsayıcısı [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) öğenin veya öğelerin temini için kullanılır.

    Projeniz VSPackage oluşturmaz çünkü onu uygulayan ortam tarafından sağlanan <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pencere VSPackage (örneğin, **Çözüm Gezgini**) kendi adına <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> yapılar.

5. Ortam, Özellikler penceresini doldurmak <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> için arabirimini temel alan nesneleri `IDispatch` almak için yöntemini çağırır. 

   Özellikler penceresindeki bir **değer** değiştirilse VSPackages, değişikliği öğe `IVsTrackSelectionEx::OnElementValueChangeEx` `IVsTrackSelectionEx::OnSelectionChangeEx` değerine rapor etmek için ve'i uygulamaya verir. Ortam daha sonra Özellikler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> penceresinde görüntülenen bilgileri özellik <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> değerleriyle **eşitlenmiş** halde tutmak için veya çağırır. Daha fazla bilgi için Özellikler [Penceresi'nin Özellik Değerlerini Güncelleştirme'ye bakın.](#updating-property-values-in-the-properties-window)

   Bu öğeyle ilgili özellikleri görüntülemek için **Çözüm Gezgini** proje öğesi seçmeye ek olarak, Özellikler penceresindeki açılan listeyi kullanarak bir form veya belge penceresinden farklı bir nesne **de seçebilirsiniz.** Daha fazla bilgi için [bkz. Özellikler Penceresi Nesne Listesi.](../../extensibility/internals/properties-window-object-list.md)

   Özellikler penceresi kılavuzunda bilgilerin alfabetikten kategorik olarak görüntülenme yolunu değiştirebilirsiniz ve varsa Özellikler penceresindeki uygun düğmelere tıklayarak seçili nesne için bir özellik sayfası da **açabilirsiniz.**  Daha fazla bilgi için [bkz. Özellikler Pencere Düğmeleri](../../extensibility/internals/properties-window-buttons.md) ve [Özellik Sayfaları.](../../extensibility/internals/property-pages.md)

   Son olarak, Özellikler **penceresinin** alt kısmında Özellikler penceresi kılavuzunda seçilen alanın **açıklaması da** vardır. Daha fazla bilgi için [bkz. Özellikler Penceresinden Alan Açıklamalarını Alma.](#getting-field-descriptions-from-the-properties-window)

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Özellikler Penceresinde Özellik Değerlerini Güncelleştirme
Özellikler penceresini özellik değeri **değişiklikleriyle** eşitlemenin iki yolu vardır. Birincisi, ortam tarafından sağlanan araç ve belge pencerelerine erişim ve oluşturma da dahil olmak üzere temel pencere işlevselliğine erişim sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimini çağırmadır. Aşağıdaki adımlar bu eşitleme işlemini açıklar.

### <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell Kullanarak Özellik Değerlerini Güncelleştirme

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell arabirimini kullanarak özellik değerlerini güncelleştirmek için

1. VSPackage'ların, projelerin veya düzenleyicilerin araç veya belge pencerelerini oluşturması veya numaralara eklemesi gereken her <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> durumda (hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> aracılığıyla) çağrısı yapmak.

2. Olayları uygulamadan ve oluşturmadan, Özellikler penceresini bir projenin özellik değişiklikleriyle (veya Özellikler penceresi tarafından göz atarak seçilen başka bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> nesneyle) eşit tutmak için   <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> uygulama.

3. yöntemlerini uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> hiyerarşinin uygulamasına gerek kalmadan sırasıyla hiyerarşi olaylarının istemci bildirimini oluşturma ve devre dışı <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> bırakma.

### <a name="updating-property-values-using-iconnection"></a>IConnection Kullanarak Özellik Değerlerini Güncelleştirme
 Özellikler penceresini özellik  değeri değişiklikleriyle eşit durumda tutmanın ikinci yolu, giden arabirimlerin var olduğunu göstermek için bağlanılabilir `IConnection` nesnede uygulamaktır. Özellik adını yerelleştirmek isterseniz nesnenizi 'den <xref:System.ComponentModel.ICustomTypeDescriptor> türetin. Uygulama, <xref:System.ComponentModel.ICustomTypeDescriptor> döndüren özellik tanımlayıcılarını değiştirebilir ve bir özelliğin adını değiştirebilir. Açıklamayı yerelleştirmek için, description özelliğinden türetilen bir öznitelik <xref:System.ComponentModel.DescriptionAttribute> oluşturun ve description özelliğini geçersiz kılın.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection arabirimini uygulamayla ilgili önemli noktalar

1. `IConnection` , bir numaralayıcı alt nesnesine arabirimiyle erişim <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> sağlar. Ayrıca, her biri arabirimi uygulayan tüm bağlantı noktası alt nesnelerine erişim <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> sağlar.

2. Herhangi bir göz atma nesnesi bir olay uygulamakla <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> sorumludur. Özellikler **penceresi** aracılığıyla ayarlanmış olay için öneride `IConnection` bulunmaktadır.

3. Bağlantı noktası, uygulamasında kaç bağlantı (bir veya daha fazla) izin verir? <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> Yalnızca bir arabirime izin veren bir bağlantı noktası <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> yönteminden <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> geri dönebilirsiniz.

4. bir istemci, `IConnection` arabirimiyle bir numaralayıcı alt nesnesine erişim elde etmek için arabirimini <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> çağırabilirsiniz. Daha <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> sonra her giden arabirim kimliği (IID) için bağlantı noktalarının numaralarını almak için arabirimi çağrılabilirsiniz.

5. `IConnection` her giden IID için arabirimiyle bağlantı noktası alt nesnelerine <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> erişim elde etmek için de çağrılabilirsiniz. Arabirim aracılığıyla bir istemci, bağlanılabilir nesne ve istemcinin kendi eşitlemesi ile bir danışmanlık döngüsü başlatır <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> veya sonlandırılır. İstemci, bildiği bağlantıları numaralandırarak arabirimiyle bir numaralayıcı nesnesi almak <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> için arabirimini de çağırabilirsiniz.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Özellikler Penceresinden Alan Açıklamalarını Alma
Özellikler penceresinin **alt kısmında,** bir açıklama alanı seçili özellik alanıyla ilgili bilgileri görüntüler. Bu özellik varsayılan olarak açıktır. Açıklama alanını gizlemek için Özellikler penceresine sağ tıklayın ve **Açıklama'ya** **tıklayın.** Bunu yapmak, menü penceresindeki Açıklama **başlığının yanındaki** onay işaretini de kaldırır. Açıklama'ya geri dönmek için aynı adımları izleyin ve alanı **yeniden** görüntüebilirsiniz.

 Açıklama alanında yer alan bilgiler ' den <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> gelir. Her yöntem, arabirim, ortak sınıf ve diğer türler tür kitaplığında yerelleştirilmiş `helpstring` olmayan bir öznitelike sahip olabilir. Özellikler **penceresi** dizeyi 'den <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> alır.

### <a name="to-specify-localized-help-strings"></a>Yerelleştirilmiş yardım dizelerini belirtmek için

1. özniteliğini `helpstringdll` tür kitaplığında kitaplık deyimine ekleyin ( `typelib` ).

   > [!NOTE]
   > Tür kitaplığı bir nesne kitaplığı (.olb) dosyasında ise bu adım isteğe bağlıdır.

2. Dizeler `helpstringcontext` için öznitelikleri belirtin. Öznitelikleri de `helpstring` belirtsiniz.

    Bu öznitelikler, gerçek .chm dosyası Yardım konularında `helpfile` `helpcontext` yer alan ve özniteliklerinden farklıdır.

   Vurgulanan özellik adı için görüntülenecek açıklama bilgilerini almak  için Özellikler penceresi seçilen özelliği çağırarak çıkış dizesi için istenen özniteliği <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> `lcid` belirtir. Dahili <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> olarak, özniteliğinde belirtilen .dll dosyasını bulur ve belirtilen bağlam `helpstringdll` .dll `DLLGetDocumentation` özniteliğiyle bu dosyada `lcid` çağrır.

   imzası ve uygulaması şu `DLLGetDocumentation` şekildedir:

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

 İşlev, `DLLGetDocumentation` DLL için .def dosyasında tanımlanan bir dışarı aktarma olması gerekir.

 Dahili olarak, aslında dll olan bir .olb dosyası oluşturulur. Bu DLL bir kaynak, tür kitaplığı (.tlb) dosyası ve dışarı aktaran bir işlev `DLLGetDocumentation` içerir.

 .olb dosyalarında özniteliği isteğe bağlıdır çünkü .tlb dosyasının kendisini içeren aynı `helpstringdll` dosyadır.

 Bu nedenle, açıklamalar bölmesinde  gösterilen dizeleri almak için, en azından tür kitaplığında `helpstring` özniteliğini belirtmeniz gerekir. Bu dizelerin yerelleştirilmiş olması için (isteğe bağlı) özniteliğini ve `helpstringdll` (gerekli) özniteliğini belirtmeniz ve `helpstringcontext` uygulaması `DLLGetDocumentation` gerekir.

 idl özniteliği ve aracılığıyla yerelleştirilmiş bilgiler elde etmek için uygulanması gereken ek arabirim `helpstringcontext` `DLLGetDocumentation` yoktur.

 Bir özelliğin yerelleştirilmiş adını ve açıklamasını almanın başka bir yolu da <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> uygulamaktır. Bu yöntemin uygulanmasıyla ilgili daha fazla bilgi için [bkz. Özellikler Penceresi Alanları ve Arabirimleri.](../../extensibility/internals/properties-window-fields-and-interfaces.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
