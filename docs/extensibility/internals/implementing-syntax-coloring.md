---
title: Sözdizimi renklendirme uygulama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cab338e253cca8c7f8457752980e7f3624317d9c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727033"
---
# <a name="implementing-syntax-coloring"></a>Söz Dizimi Renklendirmesi Uygulama
Dil hizmeti söz dizimi renklendirmesi sağlıyorsa, ayrıştırıcı bir metin satırını renklenebilir öğelerin dizisine dönüştürür ve bu renklenebilir öğelere karşılık gelen belirteç türlerini döndürür. Ayrıştırıcı, renklenebilir öğeler listesine ait olan belirteç türlerini döndürmelidir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], Colorizer nesnesinin uygun belirteç türüne göre atanan özniteliklere göre kod penceresindeki renklenebilir her öğeyi görüntüler.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir Ayrıştırıcı arabirimi belirtmez ve ayrıştırıcı uygulamasını tamamen sizin yapmanız gerekir. Ancak, Visual Studio dil paketi projesinde varsayılan bir Ayrıştırıcı uygulamasının sağlanması gerekir. Yönetilen kod için, yönetilen paket çerçevesi (MPF), metin renklendirme için kapsamlı destek sağlar.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Sözdizimi renklendirmesinin yeni yolu hakkında daha fazla bilgi edinmek için bkz. [Izlenecek yol: metin vurgulama](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Bir düzenleyiciyi Izleyen ve metni renklendirmeye yönelik adımlar

1. Düzenleyici, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> nesnesinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> yöntemini çağırarak Colorizer 'ı alır.

2. Düzenleyici, Colorizer 'ın Colorizer dışında tutulmasını sağlamak için her satırın durumunun gerekip gerekmediğini belirleme <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> yöntemini çağırır.

3. Colorizer durumunun Colorizer dışında tutulmasını gerektiriyorsa, düzenleyici ilk satırın durumunu almak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> yöntemini çağırır.

4. Arabellekte her satır için, düzenleyici aşağıdaki adımları gerçekleştiren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yöntemini çağırır:

    1. Metin satırı, metni belirteçlere dönüştürmek için tarayıcıya geçirilir. Her belirteç, belirteç metnini ve belirteç türünü belirtir.

    2. Belirteç türü bir dizine, renklenebilir öğeler listesine dönüştürülür.

    3. Belirteç bilgileri, dizideki her öğe, satırdaki bir karaktere karşılık gelen bir diziyi doldurmanız için kullanılır. Dizide depolanan değerler, renklenebilir öğeler listesindeki dizinlerdir.

    4. Satırın sonundaki durum her satır için döndürülür.

5. Colorizer durumunun tutulmasını gerektiriyorsa, düzenleyici bu satırın durumunu önbelleğe alır.

6. Düzenleyici, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> yönteminden döndürülen bilgileri kullanarak metin satırını işler. Bu, aşağıdaki adımları gerektirir:

    1. Satırdaki her bir karakter için renklendirilebilir öğe dizinini alın.

    2. Varsayılan renklenebilir öğeleri kullanıyorsanız düzenleyicinin renklenebilir öğeler listesine erişin.

    3. Aksi takdirde, renklenebilir bir öğe almak için dil hizmetinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> yöntemini çağırın.

    4. Metni ekranda işlemek için renklenebilir öğedeki bilgileri kullanın.

## <a name="managed-package-framework-colorizer"></a>Yönetilen paket çerçevesi Colorizer
 Yönetilen paket çerçevesi (MPF), bir renk Oluşturucu uygulamak için gereken tüm sınıfları sağlar. Dil hizmeti sınıfınız <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfını devralması ve gerekli yöntemleri uygulamalıdır. @No__t_0 arabirimini uygulayarak bir tarayıcı ve ayrıştırıcı sağlamanız gerekir ve bu arabirimin bir örneğini <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yönteminden (<xref:Microsoft.VisualStudio.Package.LanguageService> sınıfında uygulanması gereken yöntemlerden biri) döndürün. Daha fazla bilgi için, bkz. [eski dil hizmetinde söz dizimi renklendirme](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Özel Renklendirilebilir Öğeler](../../extensibility/internals/custom-colorable-items.md)
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)