---
title: Özellikler penceresi alanları ve arabirimleri | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706160"
---
# <a name="properties-window-fields-and-interfaces"></a>Özellikler Penceresi Alanları ve Arabirimleri
**Özellikler** penceresinde hangi bilgilerin görüntülendiğini belirlemek için seçim MODELI, IDE 'ye odaklanılmış pencereyi temel alır. Seçili penceredeki her pencere ve nesnenin seçim bağlamı nesnesi genel seçim bağlamına itilmiş olabilir. Bu pencere odağa sahip olduğunda, ortam, genel seçim bağlamını bir pencere çerçevesindeki değerlerle güncelleştirir. Odak değiştiğinde seçim bağlamını de yapar.

## <a name="tracking-selection-in-the-ide"></a>IDE 'de seçimi izleme
 IDE 'nin sahip olduğu pencere çerçevesinin veya sitenin adlı bir hizmeti vardır <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Aşağıdaki adımlarda, bir seçimdeki değişikliğin, kullanıcının odağı başka bir açık pencereye değiştirme veya **Çözüm Gezgini**' de farklı bir proje öğesi seçme, **Özellikler** penceresinde görüntüleneni değiştirmek için uygulanıp uygulanmadığı gösterilmektedir.

1. Seçili pencerede yer alan VSPackage tarafından oluşturulan nesne <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> Invoke sahibi olacak şekilde çağırır <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Seçilen pencere tarafından sunulan seçim kapsayıcısı kendi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesnesini oluşturur. Seçim değiştiğinde VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> değişikliğin **Özellikler** penceresi dahil olmak üzere ortamdaki tüm dinleyicileri bilgilendirmek için çağırır. Ayrıca, yeni seçimle ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.

3. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>' In seçili hiyerarşi öğeleri çağrısı ve geçirilmesi, `VSHPROPID_BrowseObject` <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesneyi doldurur.

4. __VSHPROPID için [IDispatch arabiriminden](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) türetilen bir nesne döndürülür [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) İstenen öğe için VSHPROPID_BrowseObject ve ortam onu bir öğesine sarmalar <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (aşağıdaki adıma bakın). Çağrı başarısız olursa, ortam bir ikinci çağrı yapar `IVsHierarchy::GetProperty` ve __VSHPROPID seçim kapsayıcısını geçer [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) Hiyerarşi öğesi veya öğelerinin tedarik VSHPROPID_SelContainer.

    <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>Ortam tarafından sağlanan Window VSPackage, onun adına (örneğin, **Çözüm Gezgini**) yapılarını kullandığından, projeniz VSPackage oluşturmaz <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

5. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `IDispatch` **Özellikler** penceresini dolduracak arabirimi temel alan nesneleri almak için yöntemlerini çağırır.

   **Properties** penceresindeki bir değer değiştirildiğinde VSPackages, `IVsTrackSelectionEx::OnElementValueChangeEx` `IVsTrackSelectionEx::OnSelectionChangeEx` değişikliği öğe değerine bildirmek için ve öğesini uygular. Daha sonra ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> **Özellikler** penceresinde görüntülenecek bilgileri özellik değerleriyle eşitlenmiş halde tutmak için veya öğesini çağırır. Daha fazla bilgi için bkz. [Özellikler penceresinde özellik değerlerini güncelleştirme](#updating-property-values-in-the-properties-window).

   Bu öğeyle ilgili özellikleri göstermek için **Çözüm Gezgini** içinde farklı bir proje öğesi seçmeye ek olarak, **Özellikler** penceresinde bulunan açılan listeyi kullanarak form veya belge penceresi içinden farklı bir nesne de seçebilirsiniz. Daha fazla bilgi için bkz. [Özellikler penceresi nesne listesi](../../extensibility/internals/properties-window-object-list.md).

   **Özellikler** penceresi kılavuzunda, bilgilerin gösterildiği biçimi alfabetik olarak kategorilere göre değiştirebilirsiniz ve varsa, **Özellikler** penceresindeki ilgili düğmelere tıklayarak seçili bir nesne için bir özellik sayfası da açabilirsiniz. Daha fazla bilgi için bkz. [Özellikler penceresi düğmeleri](../../extensibility/internals/properties-window-buttons.md) ve [Özellik sayfaları](../../extensibility/internals/property-pages.md).

   Son olarak, **Özellikler** penceresinin alt kısmında **Özellikler** penceresi kılavuzunda seçilen alanın bir açıklaması da bulunur. Daha fazla bilgi için bkz. [Özellikler penceresinden alan açıklamalarını alma](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Özellikler penceresinde özellik değerlerini güncelleştirme
**Özellikler** penceresini Özellik değeri değişiklikleriyle eşitlenmiş halde tutmanın iki yolu vardır. Birincisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ortam tarafından sağlanan araç ve Belge pencerelerinin erişimine ve oluşturulmasına dahil olmak üzere temel pencere işlevlerine erişim sağlayan arabirimi çağırmakta. Aşağıdaki adımlarda bu eşitleme işlemi açıklanır.

### <a name="updating-property-values-using-ivsuishell"></a>Isuishell kullanarak özellik değerleri güncelleştiriliyor

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Isuishell arabirimini kullanarak özellik değerlerini güncelleştirmek için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , VSPackages, proje veya düzenleyicilerin araç veya belge pencereleri oluşturması veya numaralandırması gereken her zaman çağrı (hizmet aracılığıyla).

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> **Özellikler** penceresini, olay uygulamadan ve tetiklemeden bir proje (veya **Özellikler** penceresi tarafından gözatılan diğer herhangi bir seçili nesne) için özellik değişiklikleriyle eşitlenmiş halde tutmak <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> için uygulayın <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> .

3. Yöntemi uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> hiyerarşi olayları için, hiyerarşinin uygulanmasını gerektirmeden istemci bildirimini oluşturun ve devre dışı bırakın <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .

### <a name="updating-property-values-using-iconnection"></a>IConnection kullanarak özellik değerlerini güncelleştirme
 **Özellikler** penceresini Özellik değeri değişiklikleriyle eşitlenmiş halde tutmanın ikinci yolu, `IConnection` giden arabirimlerin varlığını göstermek için bağlanılabilir nesneye uygulanır. Özellik adını yerelleştirmek isterseniz, nesnenizin içinden türetebilirsiniz <xref:System.ComponentModel.ICustomTypeDescriptor> . <xref:System.ComponentModel.ICustomTypeDescriptor>Uygulama, döndürdüğü Özellik tanımlayıcılarını değiştirebilir ve bir özelliğin adını değiştirebilir. Açıklamayı yerelleştirmek için, <xref:System.ComponentModel.DescriptionAttribute> Description özelliğinden türetilen ve geçersiz kılacak bir öznitelik oluşturun.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection arabirimini uygulama konusunda dikkat edilecek noktalar

1. `IConnection` arabirimle bir Numaralandırıcı alt nesnesine erişim sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> . Ayrıca, her biri arabirimini uygulayan tüm bağlantı noktası alt nesnelerine erişim sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> .

2. Herhangi bir tarayıcı nesnesi, bir olay uygulamaktan sorumludur <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> . **Özellikler** penceresi aracılığıyla olay kümesi için öneri alınacaktır `IConnection` .

3. Bir bağlantı noktası, uygulamasının uygulamasında kaç tane bağlantı (bir veya daha fazla) izin verdiğini denetler <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Yalnızca bir arabirime izin veren bir bağlantı noktası yönteminden dönebilir <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> .

4. Bir istemci arabirimi `IConnection` ile bir Numaralandırıcı alt nesnesine erişim elde etmek için arabirimi çağırabilir <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> . <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>Daha sonra arabirim, her giden ARABIRIM kimliği (IID) için bağlantı noktalarını numaralandırmak üzere çağrılabilir.

5. `IConnection` , bağlantı noktası alt nesnelerine <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> her gıden IID için arabirim ile erişim sağlamak için de çağrılabilir. Arabirim aracılığıyla <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> istemci, bağlanılabilir nesne ve istemcinin kendi eşitlemesine sahip bir danışmanlık döngüsünü başlatır veya sonlandırır. İstemci Ayrıca, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> bildiği bağlantıları numaralandırmak için arabirimi ile bir Numaralandırıcı nesnesi elde etmek üzere arabirimi çağırabilir.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Özellikler penceresinden alan açıklamalarını alma
**Özellikler** penceresinin alt kısmında, bir açıklama alanı seçili özellik alanı ile ilgili bilgileri görüntüler. Bu özellik varsayılan olarak açıktır. Açıklama alanını gizlemek istiyorsanız, **Özellikler** penceresine sağ tıklayın ve **Açıklama**' ya tıklayın. Bunun yapılması, Menü penceresindeki **Açıklama** başlığının yanındaki onay işaretini de kaldırır. **Açıklamayı** tekrar açmak için aynı adımları izleyerek alanı yeniden görüntüleyebilirsiniz.

 Açıklama alanındaki bilgiler öğesinden gelir <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Her yöntem, arabirim, coclass, ve benzeri, tür kitaplığında yerelleştirilmemiş bir `helpstring` özniteliğe sahip olabilir. **Özellikler** penceresi öğesinden dize alır <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Yerelleştirilmiş Yardım dizelerini belirtmek için

1. `helpstringdll`Özniteliği tür kitaplığı () içindeki kitaplık ifadesine ekleyin `typelib` .

   > [!NOTE]
   > Tür kitaplığı bir nesne kitaplığı (. olb) dosyasında ise bu adım isteğe bağlıdır.

2. `helpstringcontext`Dizelerin özniteliklerini belirtin. Öznitelikleri de belirtebilirsiniz `helpstring` .

    Bu öznitelikler, `helpfile` `helpcontext` gerçek. chm dosyası yardım konularında yer alan ve özniteliklerinden farklıdır.

   Vurgulanan Özellik adı için görüntülenecek açıklama bilgilerini almak için, **Özellikler** penceresi <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> Seçili olan özelliği çağırır ve `lcid` çıktı dizesi için istenen özniteliği belirterek. Dahili olarak, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> özniteliğinde belirtilen. dll dosyasını bulur `helpstringdll` ve `DLLGetDocumentation` belirtilen bağlam ve özniteliğe sahip bu. dll dosyasında çağırır `lcid` .

   İmzası ve uygulanması `DLLGetDocumentation` şunlardır:

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

 `DLLGetDocumentation`İşlev, DLL için. def dosyasında tanımlanmış bir dışarı aktarma olmalıdır.

 Dahili olarak, aslında DLL olan bir. olb dosyası oluşturulur. Bu DLL, bir kaynak, tür kitaplığı (. tlb) dosyası ve bir tane aktarılmış işlevi içerir `DLLGetDocumentation` .

 . Olb dosyalarında, `helpstringdll` . tlb dosyasının kendisini içeren dosya olduğu için özniteliği isteğe bağlıdır.

 **Açıklamalar** bölmesinde gösterilecek dizeleri almak için, bu nedenle yapmanız gereken en düşük değer `helpstring` tür kitaplığında özniteliği belirtmektir. Bu dizelerin yerelleştirilmesi istiyorsanız, `helpstringdll` (isteğe bağlı) özniteliğini ve `helpstringcontext` (gerekli) özniteliğini belirtmeniz ve uygulamanız gerekir `DLLGetDocumentation` .

 IDL 'nin özniteliği ve ile yerelleştirilmiş bilgileri alınırken uygulanması gereken ek arabirimler yoktur `helpstringcontext` `DLLGetDocumentation` .

 Yerelleştirilmiş adı ve bir özelliğin açıklamasını elde etmenin bir başka yolu da uygulamadır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Bu yöntemin uygulanmasıyla ilgili daha fazla bilgi için bkz. [Özellikler penceresi alanları ve arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
