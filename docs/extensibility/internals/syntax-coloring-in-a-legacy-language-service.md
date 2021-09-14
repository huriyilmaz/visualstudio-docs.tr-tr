---
title: Eski Dil Hizmeti Hizmet HizmetLerinde Söz Dizimi Renklendirmesi | Microsoft Docs
description: Dil öğelerini Visual Studio ve bunları bir düzenleyicide renklerle görüntülemek için eski dil hizmetlerinde söz dizimi renklendirme hizmetini nasıl uygulaydığını öğrenin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0444e435552fafd56b638fa7932e900498836d0d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626042"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi

Visual Studio dil öğelerini tanımlamak ve bunları bir düzenleyicide belirtilen renklerle görüntülemek için bir renklendirme hizmeti kullanır.

## <a name="colorizer-model"></a>Renklandırıcı Modeli
 Dil hizmeti, daha <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> sonra düzenleyiciler tarafından kullanılan arabirimini uygulamaya almaktadır. Bu uygulama, aşağıdaki çizimde gösterildiği gibi dil hizmetlerinden ayrı bir nesnedir:

 ![SVC Renklandırıcı grafiği](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Söz dizimi renklendirme hizmeti, metni renklendirmek Visual Studio genel renklendirme mekanizmasından ayrıdır. Renklendirmeyi destekleyen genel mekanizma [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] hakkında daha fazla bilgi için bkz. Yazı [Tiplerini ve Renkleri Kullanma.](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015)

 Renklandırıcının yanı sıra, dil hizmeti düzenleyici tarafından kullanılan özel renkleştirilebilir öğeleri özel renkleştirilebilir öğeler de sağlar. Arabirimini uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> nesnede arabirimini kullanarak bunu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> gerçekleştirebilirsiniz. Düzenleyici yöntemi çağıran özel renkleştirilebilir öğe sayısını döndürür ve düzenleyici yöntemi çağıran tek bir özel renklenebilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> öğe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> döndürür.

 yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> arabirimini uygulayan bir nesnesi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> döndürür. Dil hizmeti 24 bit veya yüksek renk değerlerini destekliyorsa arabirimini arabirimle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> aynı nesne üzerinde uygulaması <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> gerekir.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage Dil Hizmeti Renklandırıcıyı Nasıl Kullanır?

1. VSPackage uygun dil hizmetini alsa da, dil hizmeti VSPackage'ın şunları yapmalarını gerektirir:

    1. Renklendirmek üzere metni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> almak için arabirimini uygulayan bir nesnesi kullanın.

         Metin genellikle arabirimi uygulayan bir nesne kullanılarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> görüntülenir.

    2. Dil hizmeti GUID'si için VSPackage hizmet sağlayıcısını sorguarak dil hizmetini elde edersiniz. Dil hizmetleri kayıt defterinde dosya uzantısı tarafından tanımlanır.

    3. yöntemini çağırarak dil hizmetini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> ile <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> ilişkilendirme.

2. VSPackage artık renklandırıcı nesnesini aşağıdaki gibi elde eder ve kullanabilir:

    > [!NOTE]
    > Temel düzenleyiciyi kullanan VSPackage'ların bir dil hizmetinin renklandırıcı nesnelerini açıkça elde etmek zorunda değildir. Çekirdek düzenleyicinin bir örneği uygun bir dil hizmeti elde etti mi burada gösterilen tüm renklendirme görevlerini gerçekleştirir.

    1. Dil hizmetinin nesne üzerinde yöntemini çağırarak , ve arabirimlerini uygulayan dil hizmetinin renklandırıcı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> nesnesini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> alın.

    2. Belirli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> bir metin aralığına ilişkin renklandırıcı bilgilerini almak için yöntemini çağırma.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> , metin süresinde renklendirme yapılan her karakter için bir değer dizisi döndürür. Değerler, çekirdek düzenleyici tarafından bakımı yapılan varsayılan renkleştirilebilir öğe listesi veya dil hizmetinin kendisi tarafından bakımı yapılan özel bir renklenebilir öğe listesi olan renkleştirilebilir bir öğe listesine dizinlerdir.

    3. Seçilen metni görüntülemek için yöntemi tarafından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> döndürülen renklendirme bilgilerini kullanın.

> [!NOTE]
> VSPackage, dil hizmeti renklandırıcısı kullanmaya ek olarak genel amaçlı metin renklendirme Visual Studio da kullanabilir. Bu mekanizma hakkında daha fazla bilgi için [bkz. Yazı Tiplerini ve Renkleri Kullanma.](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015)

## <a name="in-this-section"></a>Bu Bölümde
- [Söz Dizimi Renklendirmesi Uygulama](../../extensibility/internals/implementing-syntax-coloring.md)

 Bir düzenleyicinin bir dil hizmetinin söz dizimi renklendirmeye nasıl erişeceklerini ve söz dizimi renklendirmeyi desteklemek için dil hizmetinin ne uygulaması gerektiğini ele almaktadır.

- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Dil hizmetlerinden yerleşik renklenebilir öğelerin nasıl kullanıla bir şekilde gösterilebilir.

- [Özel Renklendirilebilir Öğeler](../../extensibility/internals/custom-colorable-items.md)

 Özel renkleştirilebilir öğelerin nasıl uygulandığını ele alan.
