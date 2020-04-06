---
title: Sözdizimi Boyama Uygulama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707641"
---
# <a name="implementing-syntax-coloring"></a>Söz Dizimi Renklendirmesi Uygulama
Dil hizmeti sözdizimi renklendirme sağlar, parser renklenebilir öğeler bir dizi içine metin satırı dönüştürür ve bu renklenebilir öğelere karşılık gelen belirteç türleri döndürür. Parser, renklenebilir öğeler listesine ait belirteç türlerini döndürmelidir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]renklendirici nesnesi tarafından uygun belirteç türüne atanan özniteliklere göre kod penceresindeki her renklendirilebilir öğeyi görüntüler.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bir parser arabirimi belirtmez ve parser uygulaması tamamen size kalmış. Ancak, Visual Studio Dil Paketi projesinde varsayılan bir ayrıştırıcı uygulaması sağlanır. Yönetilen kod için yönetilen paket çerçevesi (MPF) metni renklendirmek için tam destek sağlar.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Sözdizimi boyama yı uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Bkz. Walkthrough: Metin Vurgulama](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Metni Renklendirmek Için Bir Düzenleyicinin İzleyin adımlar

1. Düzenleyici <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> nesne üzerinde yöntem çağırarak colorizer alır.

2. Düzenleyici, kolorizerin kolorizerin dışında tutulabilmesi için her satırın durumuna ihtiyaç dolup olmadığını belirlemek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> yöntemi çağırır.

3. Colorizer durum kolorizer dışında tutulması nı gerektiriyorsa, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> düzenleyici ilk satırın durumunu almak için yöntemi çağırır.

4. Arabellekteki her satır için düzenleyici, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> aşağıdaki adımları gerçekleştiren yöntemi çağırır:

    1. Metin satırı, metni belirteçlere dönüştürmek için tarayıcıya geçirilir. Her belirteç belirteç metnini ve belirteç türünü belirtir.

    2. Belirteç türü renklendirilebilir öğeler listesine dizin dönüştürülür.

    3. Belirteç bilgileri, dizinin her öğesinin satırdaki bir karaktere karşılık gelecek şekilde bir diziyi doldurmak için kullanılır. Dizide depolanan değerler, renklenebilir öğeler listesine dizinlerdir.

    4. Satırın sonundaki durum her satır için döndürülür.

5. Renklendirici durumunun korunmasını gerektiriyorsa, düzenleyici bu satır için durumu önbelleğe alar.

6. Düzenleyici, yöntemden döndürülen bilgileri kullanarak metin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> satırını işler. Bu, aşağıdaki adımları gerektirir:

    1. Satırdaki her karakter için renklendirilebilir madde dizini alın.

    2. Varsayılan renklendirilebilir öğeleri kullanıyorsanız, düzenleyicinin renklenebilir öğeler listesine erişin.

    3. Aksi takdirde, renklenebilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> bir öğe elde etmek için dil hizmetinin yöntemini arayın.

    4. Metni ekrana işlemek için renklenebilir öğedeki bilgileri kullanın.

## <a name="managed-package-framework-colorizer"></a>Yönetilen Paket Çerçeve Renklendirici
 Yönetilen paket çerçevesi (MPF), bir kolorizer uygulamak için gereken tüm sınıfları sağlar. Dil hizmeti sınıfınız <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı devralmalı ve gerekli yöntemleri uygulamalıdır. <xref:Microsoft.VisualStudio.Package.IScanner> Arabirimi uygulayarak bir tarayıcı ve ayrıştırıcı sağlamalı ve <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemden bu arabirimin bir örneğini döndürmeniz gerekir <xref:Microsoft.VisualStudio.Package.LanguageService> (sınıfta uygulanması gereken yöntemlerden biri). Daha fazla bilgi için, [Eski Dil Hizmetinde Sözdizimi Renklendirme'ye](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Özel Renklendirilebilir Öğeler](../../extensibility/internals/custom-colorable-items.md)
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
