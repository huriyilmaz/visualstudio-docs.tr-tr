---
title: Özellikler Penceresine Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706024"
---
# <a name="properties-window-overview"></a>Özellikler Penceresine Genel Bakış
**Özellikler** penceresi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamında (IDE) kullanılabilen iki ana pencere türünde seçilen nesnelerin özelliklerini görüntülemek için kullanılır. Bu iki tür pencere şunlardır:

- Çözüm Gezgini, Sınıf Görünümü ve Nesne tarayıcısı gibi araç pencereleri

- Form tasarımcısı, XML düzenleyicisi ve HTML düzenleyicisi gibi düzenleyicileri ve tasarımcıları içeren belge pencereleri

## <a name="using-the-properties-window"></a>Özellikler Penceresini Kullanma
 **Özellikler** penceresi, tek veya birden çok seçili öğenin özelliklerini görüntüler. Birden çok öğe seçilirse, seçili tüm nesnelerin tüm özelliklerinin kesişimi görüntülenir.

 Form tasarım penceresinde seçili bir nesneyle veya COM+ meta verilerini kullanan HTML düzenleyicisi ile ilgili olaylar **Özellikler** penceresinde görüntülenir. Örneğin, bir düğme seçebilir ve bu düğmeye bağlanabilen bir `OnClick` olay gibi ilişkili olayları görüntüleyebilirsiniz.

 **Özellikler** penceresinde görüntülenen olaylar öncelikle koda bağlı nesnelerle kullanılır. Kodla ilgisi olmayan bir dosya biçimini düzenliyorsanız, herhangi bir olay olmayacak. Olaylar yalnızca çalışan kod ile belirli nesnelerle ilişkili belirli olaylar arasında bir bağlama olduğunda **Özellikler** penceresinde görüntülenir. Bunun bir örneği, bu nesne etkinleştirildiğinde çalıştıran seçili bir nesnenin arkasındaki kod olacaktır.

 Aşağıdaki tabloda **Özellikler** penceresi tarafından kullanılan birincil arabirimleri listeler.

|Arayüz Adı|Açıklama|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|**Özellikler** penceresine bir kategori listesi sağlar ve her özelliği bir kategoriyle eşler.|
|[IDispatch Arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Nesnenin yöntemlerini ve özelliklerini programlama araçlarına ve otomasyonu destekleyen diğer uygulamalara gösterir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Nesnenin kendisi tarafından uygulanan modal iletişim pencerelerini açan *oluşturucuadı* adı verilen elips (...) düğmeleri sağlar. Bir değer bir metin alanında kullanıcı tarafından kolayca yazıldığında kullanılır. Örneğin, sizin için RGB değerini belirleyen bir renk seçici açmak için kullanılabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|**Özellikler** penceresinde görüntülenen bilgileri güncelleştirmek için kullanılan nesnelere erişim sağlar. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>görüntülenecek ilgili özelliklere sahip seçilebilir nesneler içeren her pencere için VSPackages tarafından uygulanır.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Arabirimin yöntemleri ve bir yapının alanları gibi nesnenin türü hakkında bilgi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|VSPackages'ın seçim olaylarının bildirimini almasını ve geçerli proje hiyerarşisi, öğe, öğe değeri ve komut UI bağlamı hakkında bilgi almasını sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Ortama birden çok seçime erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|**Özellikler** penceresinde görüntülenen bazı özelliklerde yerelleştirilmiş adlar sağlamak için kullanılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Kayıtlı VSPackages'ı geçerli seçim, öğe değeri veya komut UI bağlamında yapılan değişiklikleri bildirir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Geçerli seçimdeki bir değişikliğin ortamını belirtir ve yeni seçimle ilgili hiyerarşi ve madde bilgilerine erişim sağlar.|

 Daha fazla `IDispatch`bilgi için MSDN kitaplığına bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
- [Özellikler Penceresi Alanları ve Arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)
