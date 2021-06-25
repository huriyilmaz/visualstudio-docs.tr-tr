---
title: Özellikler PenceresiNe Genel Bakış | Microsoft Docs
description: Bu genel bakışta IDE'de Özellikler penceresi etkileşimde bulunmak için Visual Studio arabirimleri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0b775cbc96303f53bcd795b2121d10af83714e6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899673"
---
# <a name="properties-window-overview"></a>Özellikler Penceresine Genel Bakış
Özellikler **penceresi,** tümleşik geliştirme ortamında (IDE) kullanılabilen iki ana pencere türünde seçilen nesnelerin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özelliklerini görüntülemek için kullanılır. Bu iki tür pencere vardır:

- Çözüm Gezgini, Sınıf Görünümü ve Nesne tarayıcısı gibi araç pencereleri

- Form tasarımcısı, XML düzenleyicisi ve HTML düzenleyicisi gibi düzenleyicileri ve tasarımcıları içeren belge pencereleri

## <a name="using-the-properties-window"></a>Özellikler Penceresini Kullanma
 Özellikler **penceresi,** seçilen tek veya birden çok öğenin özelliklerini görüntüler. Birden çok öğe seçilirse, tüm seçili nesneler için tüm özelliklerin kesişimi görüntülenir.

 Form tasarım penceresinde veya COM+ meta verileri kullanan HTML düzenleyicisinde seçili bir nesneyle ilgili olaylar Özellikler **penceresinde** görüntülenir. Örneğin, bir düğmeyi seçerek ilişkili olaylarını (örneğin, bu düğmeye `OnClick` bağlanan bir olay) görüntüebilirsiniz.

 Özellikler penceresinde **görüntülenen olaylar** öncelikli olarak koda bağlı nesnelerle kullanılır. Kodla ilgili bir şey yapmayan bir dosya biçimini düzenliyorsanız hiçbir olayla ilgili olmaz. Olaylar yalnızca çalışan kod ile **belirli** nesnelerle ilişkili belirli olaylar arasında bir bağlama olduğunda Özellikler penceresinde görüntülenir. Buna örnek olarak, bu nesne etkinleştirildiğinde yürütülen seçili bir nesnenin ardındaki kod olabilir.

 Aşağıdaki tabloda Özellikler penceresi tarafından kullanılan birincil arabirimler **listeleniyor.**

|Arabirim Adı|Açıklama|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Özellikler penceresine kategorilerin listesini **sağlar** ve her özelliği bir kategoriye eşler.|
|[IDispatch Arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Bir nesnenin yöntemlerini ve özelliklerini programlama araçlarına ve otomasyonu destekleyen diğer uygulamalara gösterir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Nesnenin kendisi tarafından uygulanan kalıcı iletişim *kutusu pencerelerini* açıp oluşturucular olarak adlandırılan üç nokta (...) düğmeleri sağlar. Bir değer kullanıcı tarafından bir metin alanına kolayca yazılamayca kullanılır. Örneğin, RGB değerini sizin için belirleyen bir renk seçici açmak için kullanılabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Özellikler penceresinde görüntülenen bilgileri güncelleştirmek için kullanılan nesnelere **erişim** sağlar. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , görüntülenecek ilgili özelliklere sahip seçilebilir nesneler içeren her pencere için VSPackage'lar tarafından uygulanır.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Bir arabirimin yöntemleri ve bir yapının alanları gibi bir nesnenin türü hakkında bilgi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|VSPackage'ların seçim olayları bildirimini almalarını ve geçerli proje hiyerarşisi, öğe, öğe değeri ve komut kullanıcı arabirimi bağlamı hakkında bilgi almalarını sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Ortama birden çok seçime erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Özellikler penceresinde görüntülenen bazı özelliklerde yerelleştirilmiş adlar sağlamak **için** kullanılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Geçerli seçim, öğe değeri veya komut kullanıcı arabirimi bağlamında yapılan değişikliklerin kayıtlı VSPackage'larını bilgilendir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Geçerli seçimde bir değişikliğin ortamına bilgi sağlar ve yeni seçimle ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.|

 hakkında daha fazla bilgi `IDispatch` için bkz. MSDN kitaplığı.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
- [Özellikler Penceresi Alanları ve Arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)
