---
title: Özel düzenleyicilerde söz dizimi renklendirmesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0233873ba5d6ea2fca746f8e12f4bf693b79da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816917"
---
# <a name="syntax-coloring-in-custom-editors"></a>Özel Düzenleyicilerde Söz Dizimi Renklendirmesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Temel düzenleyici dahil Visual Studio ortamı SDK düzenleyicileri, belirli sözdizimsel öğeleri tanımlamak ve belirli bir belge görünümü için belirtilen renklerle görüntülemek için dil hizmetlerini kullanın.  
  
## <a name="colorization-requirements"></a>Renklendirme gereksinimleri  
 Bir dil hizmetinin Colorizer 'ı uygulayan tüm düzenleyiciler şunları içermelidir:  
  
1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>Renklendirilebilen metni yönetmek için uygulayan bir nesne ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> metnin belge görünümünü sağlamak için uygulayan bir nesne kullanın.  
  
2. Dil hizmetinin tanımlayıcı GUID 'INI kullanarak VSPackage 'ın hizmet sağlayıcısını sorgulayarak belirli bir dil hizmetine bir arabirim elde edin.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>Uygulayan nesnenin yöntemini çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Bu yöntem, dil hizmetini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> VSPackage 'ın, renklendirilen metni yönetmek için kullandığı uygulamayla ilişkilendirir.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Dil hizmetinin Colorizer 'ın temel Düzenleyici kullanımı  
 Colorizer içeren bir dil hizmeti, çekirdek düzenleyicinin bir örneği tarafından elde edildiğinde, sizin bölümlemeden daha fazla müdahale gerektirmeden, bir dil hizmetinin Colorizer tarafından metnin ayrıştırılması ve işlenmesi otomatik olarak gerçekleşir.  
  
 IDE saydam:  
  
- Uygulamasının uygulamasında eklendiği veya değiştirildiği şekilde metni ayrıştırmak ve analiz etmek için gereken Colorizer 'ı çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
- Uygulama tarafından sağlanan belge görünümü tarafından sağlanan görüntülemenin, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Colorizer tarafından döndürülen bilgiler kullanılarak güncelleştirildiğinden ve yeniden boyanmasını sağlar.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Dil hizmetinin Colorizer 'ın çekirdek olmayan Düzenleyici kullanımı  
 Çekirdek olmayan düzenleyici örnekleri, dil hizmetinin sözdizimi renklendirme hizmetini de kullanabilir, ancak hizmetin colorizer 'ı açıkça alıp uygulayıp, belge görünümlerinin kendisini yeniden çizmeyi gerekir.  
  
 Bunu yapmak için, için çekirdek olmayan bir düzenleyici gerekir:  
  
1. Dil hizmetinin colorizer nesnesini edinin ( `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` ve uygular <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). VSPackage, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> dil hizmetinin arabirimindeki yöntemi çağırarak bunu yapar.  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Belirli bir metin alanının renklendirilmemiş olmasını istemek için yöntemini çağırın.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Yöntemi, metin alanındaki renklendirilmiş her bir harf için bir değer dizisi döndürür. Ayrıca, metin yayılımını açıklama, anahtar sözcük veya veri türü gibi belirli bir renklendirilebilir öğe türü olarak tanımlar.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Metnini yeniden çizmek ve göstermek için tarafından döndürülen renklendirme bilgilerini kullanın.  
  
> [!NOTE]
> Bir dil hizmetinin Colorizer 'ı kullanmanın yanı sıra, VSPackage, genel amaçlı Visual Studio ortamı SDK 'Sı metin renklendirme mekanizmasını kullanmayı seçebilir. Bu mekanizma hakkında daha fazla bilgi için bkz. [yazı tiplerini ve renkleri kullanma](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmetinde söz dizimi renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Sözdizimi renklendirme uygulama](../extensibility/internals/implementing-syntax-coloring.md)   
 [Nasıl yapılır: yerleşik Renklenebilir öğeleri kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Özel Renklendirilebilir Öğeler](../extensibility/internals/custom-colorable-items.md)
