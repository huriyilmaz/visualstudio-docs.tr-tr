---
title: Eski dil hizmetinde söz dizimi renklendirmesi | Microsoft Docs
description: Visual Studio 'Nun, dilin öğelerini tanımlamak ve bunları düzenleyicide renklerle göstermek için eski dil hizmetinde bir sözdizimi renklendirme hizmetini nasıl uyguladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b8886daa5bbdd7adb03f9bf90fba7a875ab483a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080534"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi

Visual Studio, dilin öğelerini tanımlamak ve bir düzenleyicide belirtilen renklerle göstermek için bir renklendirme hizmeti kullanır.

## <a name="colorizer-model"></a>Colorizer modeli
 Dil hizmeti, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Düzenleyici tarafından kullanılan arabirimini uygular. Bu uygulama, aşağıdaki çizimde gösterildiği gibi dil hizmetinden ayrı bir nesnedir:

 ![SVC Colorizer grafiği](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Sözdizimi renklendirme hizmeti, metin renklendirme için genel Visual Studio mekanizmasından ayrıdır. Renklendirme destekleyen genel mekanizma hakkında daha fazla bilgi için [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] bkz. [yazı tipi ve renk kullanımı](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

 Colorizer 'ın yanı sıra dil hizmeti, düzenleyici tarafından kullanılan ve özel renklenebilir öğeler sağladığı özel renklenebilir öğeler sağlayabilir. Bunu, arabirimini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> uygulayan aynı nesne üzerinde arabirimini uygulayarak yapabilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> . Düzenleyici yöntemi çağırdığında özel renklenebilir öğelerin sayısını döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> ve düzenleyici yöntemi çağırdığında özel renklenebilir tek bir öğe döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>Yöntemi, arabirimini uygulayan bir nesne döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> . Dil hizmeti, 24 bit veya yüksek renk değerlerini destekliyorsa, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi arabirimi ile aynı nesne üzerinde uygulamalıdır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage bir dil hizmeti renklendirme özelliğini nasıl kullanır?

1. VSPackage 'ın, dil hizmeti VSPackage 'ın aşağıdakileri yapması için uygun dil hizmetini alması gerekir:

    1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>Renklendirilebilen metni almak için arabirimi uygulayan bir nesne kullanın.

         Metin, genellikle arabirimini uygulayan bir nesne kullanılarak görüntülenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

    2. Dil hizmeti GUID 'SI için VSPackage hizmet sağlayıcısını sorgulayarak dil hizmetini alın. Dil Hizmetleri, kayıt defterinde dosya uzantısına göre tanımlanır.

    3. Yöntemini çağırarak dil hizmetini ile ilişkilendirin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> .

2. VSPackage artık colorizer nesnesini şu şekilde alabilir ve kullanabilir:

    > [!NOTE]
    > Çekirdek düzenleyiciyi kullanan VSPackages, dil hizmetinin Colorizer nesnelerini açıkça almak zorunda değildir. Temel düzenleyicinin bir örneği uygun bir dil hizmetini edindiği anda, burada gösterilen tüm renklendirme görevlerini gerçekleştirir.

    1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Dil hizmetinin nesnesi üzerinde yöntemini çağırarak, ve arabirimlerini uygulayan dil hizmetinin colorizer nesnesini edinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .

    2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Belirli bir metin aralığı için Colorizer bilgilerini elde etmek için yöntemini çağırın.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metin alanındaki renklendirilmiş olan her karakter için bir değer dizisi döndürür. Değerler, çekirdek Düzenleyici tarafından tutulan varsayılan renklenebilir öğe listesi ya da dil hizmetinin kendisi tarafından tutulan özel renklenebilir bir öğe listesi olan renklenebilir bir öğe listesi halinde dizinlerdir.

    3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Seçili metni göstermek için yöntemi tarafından döndürülen renklendirme bilgilerini kullanın.

> [!NOTE]
> Bir dil hizmeti renklendirme kullanmanın yanı sıra, bir VSPackage, genel amaçlı Visual Studio metin renklendirme mekanizmasını de kullanabilir. Bu mekanizma hakkında daha fazla bilgi için bkz. [yazı tiplerini ve renkleri kullanma](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="in-this-section"></a>Bu Bölümde
- [Söz Dizimi Renklendirmesi Uygulama](../../extensibility/internals/implementing-syntax-coloring.md)

 Bir düzenleyicinin dil hizmetinin sözdizimi renklendirmesini ve dil hizmetinin sözdizimi renklendirmesini desteklemek için ne uygulaması gerektiğini açıklar.

- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Dil hizmetinden yerleşik renklenebilir öğelerin nasıl kullanıldığını gösterir.

- [Özel Renklendirilebilir Öğeler](../../extensibility/internals/custom-colorable-items.md)

 Özel renklenebilir öğelerin nasıl uygulanacağını açıklar.
