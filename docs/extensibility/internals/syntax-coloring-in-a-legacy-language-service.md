---
title: Eski Dil Hizmetinde Sözdizimi Boyama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704754"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi

Visual Studio, dilöğelerini tanımlamak ve editörde belirtilen renklerle görüntülemek için bir boyama hizmeti kullanır.

## <a name="colorizer-model"></a>Kolorizer Modeli
 Dil hizmeti, daha <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> sonra editörler tarafından kullanılan arabirimi uygular. Bu uygulama, aşağıdaki resimde gösterildiği gibi, dil hizmetinden ayrı bir nesnedir:

 ![SVC Kolorezer grafiği](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Sözdizimi boyama hizmeti, metni renklendirmek için genel Visual Studio mekanizmasından ayrıdır. Renklendirmeyi destekleyen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] genel mekanizma hakkında daha fazla bilgi için [bkz.](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)

 Colorizer yanı sıra, dil hizmeti özel renklenebilir öğeleri temin reklam, editör tarafından kullanılan özel renklenebilir öğeleri sağlayabilir. Bunu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirimi uygulayan nesne üzerinde arabirimi uygulayarak yapabilirsiniz. Düzenleyici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> yöntemi aradığında özel renklendirilebilir öğelerin sayısını döndürür ve düzenleyici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> yöntemi aradığında tek bir özel renklendirilebilir öğedöndürür.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Yöntem, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> arabirimi uygulayan bir nesne döndürür. Dil hizmeti 24 bit veya yüksek renk değerlerini destekliyorsa, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimi arabirimle aynı nesneye uygulamalıdır.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage Dil Hizmeti Renklendirici Nasıl Kullanır?

1. VSPackage aşağıdakileri yapmak için dil hizmeti VSPackage gerektiren uygun dil hizmeti almalısınız:

    1. Metnin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> renklendirilmesi için arabirimi uygulayan bir nesne kullanın.

         Metin genellikle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimi uygulayan bir nesne kullanılarak görüntülenir.

    2. Dil hizmeti GUID için VSPackage servis sağlayıcısını sorgulayarak dil hizmetini alın. Dil hizmetleri dosya uzantısı tarafından kayıt defterinde tanımlanır.

    3. Dil hizmetini yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> çağırarak ilişkilendirin.

2. VSPackage artık colorizer nesnesini aşağıdaki gibi alabilir ve kullanabilir:

    > [!NOTE]
    > Çekirdek düzenleyiciyi kullanan VSPackages açıkça bir dil hizmeti nin renklendirici nesneleri elde etmek zorunda değilsiniz. Çekirdek düzenleyicinin bir örneği uygun bir dil hizmeti alır almaz, burada gösterilen tüm renklendirme görevlerini gerçekleştirir.

    1. Dil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>hizmetinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> nesnesi üzerindeki yöntemi arayarak, dil hizmetinin renklendirici nesnesini ve arabirimleri uygulayan renklendirici nesnesini edinin.

    2. Belirli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> bir metin aralığı için renklendirici bilgilerini elde etmek için yöntemi arayın.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>renklendirilmekte olan metin aralığındaki her karakter için bir dizi değer verir. Değerler, çekirdek düzenleyici tarafından tutulan varsayılan renklenebilir öğe listesi veya dil hizmetinin kendisi tarafından tutulan özel renklendirilebilir öğe listesi olan renklenebilir madde listesine dizinlerdir.

    3. Seçili metni görüntülemek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemtarafından döndürülen renklendirme bilgilerini kullanın.

> [!NOTE]
> Bir dil hizmeti renklendirici kullanmanın yanı sıra, bir VSPackage da genel amaçlı Visual Studio metin boyama mekanizması kullanabilirsiniz. Bu mekanizma hakkında daha fazla bilgi için Yazı [Tiplerini ve Renkleri Kullanma'ya](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)bakın.

## <a name="in-this-section"></a>Bu Bölümde
- [Söz Dizimi Renklendirmesi Uygulama](../../extensibility/internals/implementing-syntax-coloring.md)

 Düzenleyicinin bir dil hizmetinin sözdizimi boyama sına nasıl eriştiğini ve sözdizimi boyama' yı desteklemek için dil hizmetinin neleri uygulaması gerektiğini tartışır.

- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Dil hizmetinden yerleşik renklenebilir öğelerin nasıl kullanılacağını gösterir.

- [Özel Renklendirilebilir Öğeler](../../extensibility/internals/custom-colorable-items.md)

 Özel renklendirilebilir öğelerin nasıl uygulanacağını tartışır.
