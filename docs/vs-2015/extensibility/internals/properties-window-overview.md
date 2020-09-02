---
title: Özellikler penceresine genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd4be229338d1a09c22b4d81384dc90f0544fa39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700751"
---
# <a name="properties-window-overview"></a>Özellikler Penceresine Genel Bakış
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Özellikler** penceresi, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tümleşik GELIŞTIRME ortamında (IDE) kullanılabilen iki ana Windows türünde seçilen nesneler için özellikleri göstermek üzere kullanılır. Bu iki tür pencere şunlardır:  
  
- Çözüm Gezgini, Sınıf Görünümü ve nesne tarayıcısı gibi araç pencereleri  
  
- Form Tasarımcısı, XML Düzenleyicisi ve HTML Düzenleyicisi olarak böyle düzenleyiciler ve tasarımcıları içeren belge pencereleri  
  
## <a name="using-the-properties-window"></a>Özellikler penceresini kullanma  
 **Özellikler** penceresi, seçilen tek veya birden çok öğenin özelliklerini görüntüler. Birden çok öğe seçilirse, seçilen tüm nesneler için tüm özelliklerin kesişimi görüntülenir.  
  
 Form Tasarım penceresi veya COM+ meta verilerini kullanan HTML Düzenleyicisi içindeki seçili nesneyle ilgili olaylar, **Özellikler** penceresinde görüntülenir. Örneğin, bir düğme seçebilir ve `OnClick` söz konusu düğmeye bağlanabilen bir olay gibi ilişkili olaylarını görüntüleyebilirsiniz.  
  
 **Özellikler** penceresinde görüntülenen olaylar öncelikle koda bağlanan nesnelerle birlikte kullanılır. Kodla ilgili hiçbir şey olmayan bir dosya biçimini düzenliyorsanız, herhangi bir olayınıza sahip olursunuz. Olaylar yalnızca çalışan kod ve belirli nesnelerle ilişkili belirli olaylar arasında bir bağlama olduğunda **Özellikler** penceresinde görüntülenir. Bu nesnenin bir örneği, nesne etkinleştirildiğinde yürütülen seçili bir nesnenin arkasında kod olabilir.  
  
 Aşağıdaki tabloda, **Özellikler** penceresi tarafından kullanılan birincil arabirimler listelenmektedir.  
  
|Arabirim adı|Description|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|**Özellikler** penceresine kategorilerin bir listesini sağlar ve her bir özelliği bir kategoriye eşler.|  
|[IDispatch arabirimi](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Programlama araçları ve otomasyonu destekleyen diğer uygulamalar için bir nesnenin yöntemlerini ve özelliklerini gösterir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Nesnenin kendisi tarafından uygulanan kalıcı iletişim kutusu pencerelerini açan *oluşturucular* adlı üç nokta (...) düğmelerini sağlar. Bir değer bir metin alanındaki Kullanıcı tarafından kolayca yazılmadığından kullanılır. Örneğin, sizin için RGB değerini belirleyen bir renk seçici açmak için kullanılabilir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|**Özellikler** penceresinde görüntülenecek bilgileri güncelleştirmek için kullanılan nesnelere erişim sağlar. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , ilgili özelliklerle birlikte seçilebilir nesneler içeren her bir pencere için VSPackages tarafından uygulanır.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Bir arabirimin yöntemleri ve bir yapı alanları gibi bir nesnenin türü hakkında bilgi sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|VSPackages 'in seçim olaylarının bildirimini almasını ve geçerli proje hiyerarşisi, öğe, öğe değeri ve komut UI bağlamı hakkında bilgi almasını sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Çoklu seçimlere erişimi olan ortamı sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|**Özellikler** penceresinde görünen bazı özelliklerde yerelleştirilmiş adlar sağlamak için kullanılır.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Geçerli seçim, öğe değeri veya komut Kullanıcı arabirimi bağlamındaki değişiklikleri kayıtlı VSPackages 'e bildirir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Geçerli seçimdeki bir değişikliğin ortamına bildirir ve yeni seçimle ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.|  
  
 Hakkında daha fazla bilgi için `IDispatch` MSDN Kitaplığı ' na bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri genişletme](../../extensibility/internals/extending-properties.md)   
 [Özellikler Penceresi Alanları ve Arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)
