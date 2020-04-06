---
title: Özel Editörlerde Sözdizimi Boyama | Microsoft Dokümanlar
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
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699334"
---
# <a name="syntax-coloring-in-custom-editors"></a>Özel Düzenleyicilerde Söz Dizimi Renklendirmesi
Çekirdek düzenleyici de dahil olmak üzere Visual Studio Environment SDK editörleri, belirli sözdizimsel öğeleri tanımlamak ve belirli bir belge görünümü için belirli renklerle görüntülemek için dil hizmetlerini kullanır.

## <a name="colorization-requirements"></a>Renklendirme Gereksinimleri
 Bir dil hizmetinin renklendirici uygulayan tüm editörler gerekir:

1. Rengiyapılacak metni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> yönetmek için bir nesne ve metnin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> belge görünümünü sağlamak için bir nesne uygulayın.

2. Diller servisinin tanımlayıcı GUID'ini kullanarak VSPackage'ın servis sağlayıcısını sorgulayarak belirli bir dil hizmetiiçin bir arabirim edinin.

3. Nesneuygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> yöntemini çağırın. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Bu yöntem, dil hizmetini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> VSPackage'ın renklendirilecek metni yönetmek için kullandığı uygulamayla ilişkilendirir.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Bir Dil Servisinin Kolorizerinin Çekirdek Editörü Kullanımı
 Bir koloratör ile bir dil hizmeti çekirdek düzenleyici bir örnek tarafından elde edildiğinde, ayrıştırma ve bir dil hizmeti nin koloratör tarafından metin render otomatik olarak sizin açınızdan başka bir müdahale gerektirmeden oluşur.

 IDE saydam olarak:

- Uygulamada eklenen veya değiştirilen metni ayrıştırmak ve çözümlemek için gerektiğinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>renklendirici yi çağırır.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Uygulama tarafından sağlanan belge görünümü tarafından sağlanan ekranın güncelleştirilmesini ve renklendirici tarafından döndürülen bilgiler kullanılarak yeniden boyanmasını sağlar.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Bir Dil Hizmetinin Colorizer'ının Çekirdek Dışı Düzenleyici Kullanımı
 Çekirdek olmayan düzenleyici örnekleri de bir dil hizmetinin sözdizimi renklendirme hizmetini kullanabilir, ancak hizmetin renklendiricisini açıkça alıp uygulamalı ve belge görünümlerini kendileri yeniden boyamalıdır.

 Bunu yapmak için çekirdek olmayan bir düzenleyici olmalıdır:

1. Bir dil hizmetinin kolorizer nesnesini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>edinin (uygular ve ). VSPackage bunu, dil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> hizmetinin arabirimindeki yöntemi arayarak yapar.

2. Belirli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> bir metin aralığının renklendirilmesini istemek için yöntemi arayın.

     Yöntem, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> renklendirilmekte olan metin aralığındaki her harf için bir dizi değer döndürür. Ayrıca metin açıklığı, yorum, anahtar kelime veya veri türü gibi belirli bir renklendirilebilir öğe türü olarak tanımlar.

3. Metnini yeniden boyamak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> ve görüntülemek için döndürülen renklendirme bilgilerini kullanın.

> [!NOTE]
> Bir dil hizmetinin renklendiricisini kullanmanın yanı sıra, BIR VSPackage genel amaçlı Visual Studio Environment SDK metin boyama mekanizmasını kullanmayı seçebilir. Bu mekanizma hakkında daha fazla bilgi için Yazı [Tiplerini ve Renkleri Kullanma'ya](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Söz Dizimi Renklendirmesi Uygulama](../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Özel Renklendirilebilir Öğeler](../extensibility/internals/custom-colorable-items.md)
