---
title: Özel düzenleyicilerde söz dizimi renklendirmesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4f6214aa67040a4eb7a4b781cf1612762c87b2e
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012431"
---
# <a name="syntax-coloring-in-custom-editors"></a>Özel Düzenleyicilerde Söz Dizimi Renklendirmesi
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
 Çekirdek olmayan düzenleyici örnekleri, dil hizmetinin sözdizimi renklendirme hizmetini de kullanabilir, ancak hizmetin colorizer 'ı açıkça alıp uygulaması ve belge görünümlerinin kendilerini yeniden örneklendirmeleri gerekir.

 Bunu yapmak için, çekirdek olmayan bir düzenleyicide şunları yapmanız gerekir:

1. Dil hizmetinin colorizer nesnesini edinin ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ve uygular <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). VSPackage bunu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> dil hizmetinin arabirimindeki yöntemini çağırarak yapar.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Belirli bir metin alanının renklendirilmemiş olmasını istemek için yöntemini çağırın.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Yöntemi, metin alanındaki renklendirilmiş her bir harf için bir değer dizisi döndürür. Ayrıca, metin yayılımını açıklama, anahtar sözcük veya veri türü gibi belirli bir renklendirilebilir öğe türü olarak tanımlar.

3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Metnini yeniden çizmek ve göstermek için tarafından döndürülen renklendirme bilgilerini kullanın.

> [!NOTE]
> Bir dil hizmetinin Colorizer 'ı kullanmanın yanı sıra, VSPackage, genel amaçlı Visual Studio ortamı SDK 'Sı metin renklendirme mekanizmasını kullanmayı seçebilir. Bu mekanizma hakkında daha fazla bilgi için bkz. [yazı tiplerini ve renkleri kullanma](../vs-2015/extensibility/using-fonts-and-colors.md?view=vs-2015).

## <a name="see-also"></a>Ayrıca bkz.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Söz Dizimi Renklendirmesi Uygulama](../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Özel Renklendirilebilir Öğeler](../extensibility/internals/custom-colorable-items.md)