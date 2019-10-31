---
title: Eski dil hizmetinde söz dizimi renklendirmesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa3dcadfc7774766c0e76617ce133d2c30ba2aa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186314"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi

Visual Studio, dilin öğelerini tanımlamak ve bir düzenleyicide belirtilen renklerle göstermek için bir renklendirme hizmeti kullanır.

## <a name="colorizer-model"></a>Colorizer modeli
 Dil hizmeti, düzenleyiciler tarafından kullanılan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimini uygular. Bu uygulama, aşağıdaki çizimde gösterildiği gibi dil hizmetinden ayrı bir nesnedir:

 ![SVC Colorizer grafiği](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Sözdizimi renklendirme hizmeti, metin renklendirme için genel Visual Studio mekanizmasından ayrıdır. Renklendiriyi destekleyen genel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mekanizması hakkında daha fazla bilgi için bkz. [yazı tipi ve renk kullanımı](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Colorizer 'ın yanı sıra dil hizmeti, düzenleyici tarafından kullanılan ve özel renklenebilir öğeler sağladığı özel renklenebilir öğeler sağlayabilir. Bunu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirimini uygulayan aynı nesne üzerinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> arabirimini uygulayarak yapabilirsiniz. Düzenleyici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> yöntemini çağırdığında özel renklenebilir öğelerin sayısını döndürür ve düzenleyici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> yöntemini çağırdığında özel renklenebilir tek bir öğe döndürür.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimini uygulayan bir nesne döndürür. Dil hizmeti, 24 bit veya yüksek renk değerlerini destekliyorsa, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimiyle aynı nesne üzerinde uygulamalıdır.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage bir dil hizmeti renklendirme özelliğini nasıl kullanır?

1. VSPackage 'ın, dil hizmeti VSPackage 'ın aşağıdakileri yapması için uygun dil hizmetini alması gerekir:

    1. Renklendirilmemiş metni almak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> arabirimini uygulayan bir nesne kullanın.

         Metin genellikle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimini uygulayan bir nesne kullanılarak görüntülenir.

    2. Dil hizmeti GUID 'SI için VSPackage hizmet sağlayıcısını sorgulayarak dil hizmetini alın. Dil Hizmetleri, kayıt defterinde dosya uzantısına göre tanımlanır.

    3. Dil hizmetini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> yöntemini çağırarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> ile ilişkilendirin.

2. VSPackage artık colorizer nesnesini şu şekilde alabilir ve kullanabilir:

    > [!NOTE]
    > Çekirdek düzenleyiciyi kullanan VSPackages, dil hizmetinin Colorizer nesnelerini açıkça almak zorunda değildir. Temel düzenleyicinin bir örneği uygun bir dil hizmetini edindiği anda, burada gösterilen tüm renklendirme görevlerini gerçekleştirir.

    1. Dil hizmetinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> nesnesindeki <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> yöntemini çağırarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> arabirimlerini uygulayan dil hizmetinin colorizer nesnesini edinin.

    2. Belirli bir metin aralığı için Colorizer bilgilerini almak üzere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemini çağırın.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, metin alanındaki renklendirilmiş her bir karakter için bir değer dizisi döndürür. Değerler, çekirdek Düzenleyici tarafından tutulan varsayılan renklenebilir öğe listesi ya da dil hizmetinin kendisi tarafından tutulan özel renklenebilir bir öğe listesi olan renklenebilir bir öğe listesi halinde dizinlerdir.

    3. Seçili metni göstermek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemi tarafından döndürülen renklendirme bilgilerini kullanın.

> [!NOTE]
> Bir dil hizmeti renklendirme kullanmanın yanı sıra, bir VSPackage, genel amaçlı Visual Studio metin renklendirme mekanizmasını de kullanabilir. Bu mekanizma hakkında daha fazla bilgi için bkz. [yazı tiplerini ve renkleri kullanma](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>Bu Bölümde
- [Söz Dizimi Renklendirmesi Uygulama](../../extensibility/internals/implementing-syntax-coloring.md)

 Bir düzenleyicinin dil hizmetinin sözdizimi renklendirmesini ve dil hizmetinin sözdizimi renklendirmesini desteklemek için ne uygulaması gerektiğini açıklar.

- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Dil hizmetinden yerleşik renklenebilir öğelerin nasıl kullanıldığını gösterir.

- [Özel Renklendirilebilir Öğeler](../../extensibility/internals/custom-colorable-items.md)

 Özel renklenebilir öğelerin nasıl uygulanacağını açıklar.