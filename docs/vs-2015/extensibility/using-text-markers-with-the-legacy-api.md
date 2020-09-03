---
title: Eski API ile metin Işaretleyicileri kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695473"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Eski API ile Metin İşaretçilerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin işaretçisi, bir metin bölgesinin görüntülenmesini ve davranışını etkileyebilecek bir arabellekteki metin aralığıdır. İşaretleyiciler kesme noktaları, yer işaretleri, dalgalı alt çizgiler ve salt okunurdur bölgeleri içerir. Metin işaretçileri, temel olarak sözdizimi renklendirinden farklıdır. Sözdizimi renklendirme, bir metin bölgesiyle ilişkili dil söz dizimini iletmenin hızlı bir yoludur. Windows ekranı bir ekran tarafından onarılmaya önemli olduğunda sözdizimi renklendirme genellikle istenir. Sözdizimi renklendirme yalnızca metin rengini değiştirir. Metin işaretçileri, diğer birçok metin özelliğini değiştirebilir. Metin işaretçileri "float" yapabilir ve özel davranış ve renklendirme uygulayabilir.  
  
 Metin işaretçileriyle ilişkili performans yükü nedeniyle, metin arabelleklerinizi için çok sayıda işaretleyici oluşturmayın. Her işaretleyici Kullanıcı arabellek içeriğini her düzenleilişinde güncelleştirilir.  
  
> [!NOTE]
> Kullanıcılar görünür işaret türünün rengini değiştirebilir, ancak şeklini ve stilini değiştirmez. Daha fazla bilgi için bkz. [yazı tipleri ve renkler, ortam, Seçenekler Iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl Yapılır: Standart Metin İşaretçileri Ekleme](../extensibility/how-to-add-standard-text-markers.md)|Bir metin görünümüne çekirdek Düzenleyici tarafından sunulan standart bir metin işaretçisi türünün nasıl ekleneceğini açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|[Nasıl Yapılır: Hata İşaretçilerini Uygulama](../extensibility/how-to-implement-error-markers.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Kırmızı dalgalı alt çizgileri kullanarak hataları göstermek için kullanılan bir işaret örneğinin nasıl uygulanacağını açıklar.|  
|[Nasıl yapılır: Özel Metin İşaretçileri Oluşturma](../extensibility/how-to-create-custom-text-markers.md)|Bir metin görünümüne özel metin işaretçisi türü oluşturmayı ve eklemeyi açıklar.|  
|[Nasıl Yapılır: Metin İşaretçileri Kullanma](../extensibility/how-to-use-text-markers.md)|Metin işaretlerinin nasıl ekleneceğini açıklar.|  
|[Temel Düzenleyicinin İçinde](../extensibility/inside-the-core-editor.md)|Çekirdek düzenleyicinin özelliklerini açıklar ve çekirdek düzenleyicinin nasıl özelleştirileceğine ilişkin ayrıntıları sağlar.|  
|[Düzenleyici Özellikleri](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Çekirdek düzenleyicide kullanılabilen özellikleri açıklar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Düzenleyici tarafından önceden tanımlanmış veya VSPackage tarafından kaydedilen belirli bir metin işaretçisi türü hakkında bilgi almak için Tekdüzen bir mekanizma sağlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 İki boyutlu koordinatları kullanarak metin arabelleğindeki metin işaretçisinin konumunu erişim sağlar ve ayarlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Metin işaretleyicilerini yönetmek için yöntemler sağlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]IDE ve metin işaretçisini ayarlamak için kullanılan diğer işlemlere geri çağrılar sağlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>Ek geri çağrılar sağlayarak arabirim aracılığıyla kullanılabilen işlevselliği genişletir.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>Ek geri çağrılar sağlayarak arabirim aracılığıyla kullanılabilen işlevselliği genişletir.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Diğer işaret türlerinin aynı renk kümesini paylaşıp paylaşmadığını belirlemede işaret türü sağlar.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Çekirdek düzenleyicide metin işaretçileri için bağlam sağlar. Çekirdek düzenleyicide bulunan her metin işaretleyici türü için, IDE ayrı bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> nesne oluşturur.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Simgeleri sürükle ve bırak düzenlemesini destekleyen işaretçiler için belirtilen bir işleyici. Glif, bir işaretin konumunu gösteren bir simgedir.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>Diğer VSPackages 'e metin işaretçileri sağlayan hizmetten bir arabirim döndürür.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Tek boyutlu koordinatları kullanarak metin arabelleğindeki metin işaretçisinin konumunu erişim sağlar ve ayarlar. Mümkünse, bu arabirimi kullanmayın.
