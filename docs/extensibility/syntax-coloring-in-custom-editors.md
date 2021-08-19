---
title: Özel Düzenleyicilerde Söz Dizimi Renklendirmesi | Microsoft Docs
description: Belirli bir belge görünümü için belirtilen renkleri Visual Studio Ortam SDK'sı özel düzenleyicileri'nde söz dizimi renklendirmesi hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 21710df4971581f95e82ff394b4880c262dd7bf3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158118"
---
# <a name="syntax-coloring-in-custom-editors"></a>Özel Düzenleyicilerde Söz Dizimi Renklendirmesi
Visual Studio Temel düzenleyici de dahil olmak üzere Ortam SDK'sı düzenleyicileri, belirli bir bozulmamış öğeleri tanımlamak ve belirli bir belge görünümü için belirtilen renklerle görüntülemek için dil hizmetlerini kullanır.

## <a name="colorization-requirements"></a>Renklendirme Gereksinimleri
 Dil hizmetinin renklandırıcısı uygulayan tüm düzenleyicilerin:

1. Renklendirmek üzere metni ve metnin belge görünümünü sağlamak üzere uygulayan bir nesneyi yönetmek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için bir nesnesi kullanın.

2. Dil hizmetinin tanımlayıcı GUID'lerini kullanarak VSPackage'ın hizmet sağlayıcısını sorgular ve belirli bir dil hizmetine arabirim elde edin.

3. uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> nesnesinin yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> çağırma. Bu yöntem, dil hizmetini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> VSPackage'ın renklendirmek için kullanılan metni yönetmek için kullandığı uygulamayla ilişkilendirmektedir.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Dil Hizmetinin Renklandırıcısı Için Temel Düzenleyici Kullanımı
 Renklandırıcıya sahip bir dil hizmeti, çekirdek düzenleyicinin bir örneği tarafından edinilirse, dil hizmetinin renklandırıcısı tarafından metin ayrıştırma ve işleme işlemi sizin tarafınıza daha fazla müdahale gerekmeden otomatik olarak gerçekleşir.

 IDE saydam bir şekilde:

- Uygulamasında eklenen veya değiştirilen metinleri ayrıştırmak ve analiz etmek için gerektiğinde renklandırıcıyı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> çağıran.

- Uygulama tarafından sağlanan belge görünümü tarafından sağlanan görünümün, renklandırıcı tarafından döndürülen bilgiler kullanılarak güncelleştirilmiş <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ve yeniden boyanmış olduğunu sağlar.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Dil Hizmetinin Renklandırıcısı Çekirdek Olmayan Düzenleyici Kullanımı
 Çekirdek olmayan düzenleyici örnekleri bir dil hizmetinin söz dizimi renklendirme hizmetini de kullanabilir, ancak hizmetin renklandırıcısını açıkça almaları ve uygulamaları ve belge görünümlerini kendileri yeniden boyamaları gerekir.

 Bunu yapmak için çekirdek olmayan bir düzenleyicinin şunları yapmaları gerekir:

1. Bir dil hizmetinin renklandırıcı nesnesini (ve uygulayan) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> alın. VSPackage bunu dil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> hizmetinin arabiriminde yöntemini çağırarak yapar.

2. Belirli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> bir metin aralığı renklendirmesini talep etmek için yöntemini çağırma.

     yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metin süresinde renklendirme yapılan her harf için bir değer dizisi döndürür. Ayrıca metin yayma özelliğini açıklama, anahtar sözcük veya veri türü gibi belirli bir renk değiştirilebilir öğe türü olarak tanımlar.

3. Yeniden boyamak ve metnini görüntülemek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> için tarafından döndürülen renklendirme bilgilerini kullanın.

> [!NOTE]
> VSPackage, dil hizmetinin renklandırıcısı kullanmanın yanı sıra Ortam SDK'sı metin renklendirme mekanizmasını Visual Studio amaçlı renklendirme mekanizmasını kullanmayı da seçebilir. Bu mekanizma hakkında daha fazla bilgi için [bkz. Yazı Tiplerini ve Renkleri Kullanma.](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>Ayrıca bkz.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Söz Dizimi Renklendirmesi Uygulama](../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Özel Renklendirilebilir Öğeler](../extensibility/internals/custom-colorable-items.md)