---
title: Özel düzenleyicilerde söz dizimi renklendirmesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302f463d93776d17be0251e6194375c15adc19
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718761"
---
# <a name="syntax-coloring-in-custom-editors"></a>Özel Düzenleyicilerde Söz Dizimi Renklendirmesi
Temel düzenleyici dahil Visual Studio ortamı SDK düzenleyicileri, belirli sözdizimsel öğeleri tanımlamak ve belirli bir belge görünümü için belirtilen renklerle görüntülemek için dil hizmetlerini kullanın.

## <a name="colorization-requirements"></a>Renklendirme gereksinimleri
 Bir dil hizmetinin Colorizer 'ı uygulayan tüm düzenleyiciler şunları içermelidir:

1. Renklendirilebilen metni yönetmek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> uygulayan bir nesne ve metnin belge görünümünü sağlamak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uygulayan bir nesne kullanın.

2. Dil hizmetinin tanımlayıcı GUID 'INI kullanarak VSPackage 'ın hizmet sağlayıcısını sorgulayarak belirli bir dil hizmetine bir arabirim elde edin.

3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>uygulayan nesnenin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> yöntemini çağırın. Bu yöntem, dil hizmetini VSPackage 'ın renklendirilmiş olacak metni yönetmek için kullandığı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> uygulamayla ilişkilendirir.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Dil hizmetinin Colorizer 'ın temel Düzenleyici kullanımı
 Colorizer içeren bir dil hizmeti, çekirdek düzenleyicinin bir örneği tarafından elde edildiğinde, sizin bölümlemeden daha fazla müdahale gerektirmeden, bir dil hizmetinin Colorizer tarafından metnin ayrıştırılması ve işlenmesi otomatik olarak gerçekleşir.

 IDE saydam:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>uygulamasında eklendiğinde veya değiştirildiğinde metni ayrıştırmak ve analiz etmek için gerektiğinde Colorizer 'ı çağırır.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uygulamasının sağladığı belge görünümü tarafından sağlanan görüntülemenin, Colorizer tarafından döndürülen bilgiler kullanılarak güncelleştirildiğinden ve yeniden boyanmasını sağlar.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Dil hizmetinin Colorizer 'ın çekirdek olmayan Düzenleyici kullanımı
 Çekirdek olmayan düzenleyici örnekleri, dil hizmetinin sözdizimi renklendirme hizmetini de kullanabilir, ancak hizmetin colorizer 'ı açıkça alıp uygulaması ve belge görünümlerinin kendilerini yeniden örneklendirmeleri gerekir.

 Bunu yapmak için, çekirdek olmayan bir düzenleyicide şunları yapmanız gerekir:

1. Dil hizmetinin colorizer nesnesini edinin (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>uygulayan). VSPackage, dil hizmetinin arabirimindeki <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> yöntemini çağırarak bunu yapar.

2. Belirli bir metin alanının renklendirilmemiş olmasını istemek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemini çağırın.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemi, bir değer dizisi döndürür. metin alanındaki her bir harf için bir değer, renklendirilir. Ayrıca, metin yayılımını açıklama, anahtar sözcük veya veri türü gibi belirli bir renklendirilebilir öğe türü olarak tanımlar.

3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> tarafından döndürülen renklendirme bilgilerini kullanarak metnini yeniden boyamak ve görüntüleyin.

> [!NOTE]
> Bir dil hizmetinin Colorizer 'ı kullanmanın yanı sıra, VSPackage, genel amaçlı Visual Studio ortamı SDK 'Sı metin renklendirme mekanizmasını kullanmayı seçebilir. Bu mekanizma hakkında daha fazla bilgi için bkz. [yazı tiplerini ve renkleri kullanma](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Söz Dizimi Renklendirmesi Uygulama](../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Özel Renklendirilebilir Öğeler](../extensibility/internals/custom-colorable-items.md)