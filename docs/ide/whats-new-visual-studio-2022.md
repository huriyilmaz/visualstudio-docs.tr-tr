---
title: Visual Studio 2022 'de (Önizleme) yapılan yeniler
titleSuffix: ''
description: Visual Studio 2022'nin önizleme Visual Studio öğrenin.
ms.date: 10/12/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: ''
ms.prod: visual-studio-dev17
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 519c5ea88164ccd3a46d7e6bf46ae56399e7d5b2
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969599"
---
# <a name="whats-new-in-visual-studio-2022-preview"></a>Visual Studio 2022 'de (Önizleme) yapılan yeniler

**17.0 Önizleme 5/Sürüm Adayı (RC) için güncelleştirildi.** Tüm [sürüm notlarına bakın |](/visualstudio/releases/2022/release-notes-preview/) Ürün [yol haritasını görüntüleme](/visualstudio/productinfo/vs-roadmap/)

>[!div class="button"]
>[2022 Preview Visual Studio indirme](https://visualstudio.microsoft.com/vs/preview/vs2022/)

Bu Visual Studio, her zaman herhangi bir geliştirici, herhangi bir uygulama ve herhangi bir platform için en iyi sınıfının araç ve hizmetlerini elde edin. İster ilk kez Visual Studio ister yıllardır kullanıyor olun, şu anda Önizleme sürümünde olan en yeni sürümde olduğu gibi çok fazla şey vardır.

## <a name="performance-improvements"></a>Performans geliştirmeleri

Visual Studio 2022 hem öğrenciler hem de endüstriyel ölçek çözümlerine sahip olanlar için tasarlanmıştır.

### <a name="visual-studio-2022-is-64-bit"></a>Visual Studio 2022 64 bittir

Visual Studio 2022 Windows artık 64 bitlik bir uygulamadır. Bu, belleğin yetersiz kalmadan en büyük ve en karmaşık çözümleri bile aç, düzenle, çalıştır ve hata ayıkla. Daha fazla bilgi edinmek için hem [Visual Studio 2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/) vision hem [de Visual Studio 2022 Preview 1](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/) blog gönderilerini okuyun.

### <a name="find-in-files-is-faster"></a>Dosyalarda Bul daha hızlıdır

[2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)Visual Studio 4'te ise birkaç temel özelliğin performansını geliştirmeye odaklandım. Örneğin, [Dosyalarda Bul artık](find-in-files.md) Core gibi büyük çözümler aranırken 3 kat daha [hızlıdır.](https://github.com/OrchardCMS/OrchardCore)

:::image type="content" source="media/vs-2022/find-files-faster.gif" alt-text="Büyük bir C# çözümünde önceki sürümden üç kat daha hızlı arama yaptığı için Dosyalarda Bul özelliğinin animasyonu Visual Studio.":::

## <a name="build-modern-apps"></a>Modern uygulamalar oluşturma

Visual Studio 2022, Azure ile modern, bulut tabanlı uygulamalar derlemeyi hızlı ve kolay bir şekilde sağlar. Ayrıca, yeni sürümümz .NET 6'ya ve hem web, istemci hem de Mac geliştiricileri için web, istemci ve mobil uygulamalar için birleşik çerçevesine tam Windows desteğine de sahip. Ayrıca Visual Studio 2022' de yeni üretkenlik özellikleri, C++20 aracı ve IntelliSense ile C++ iş yükü için sağlam destek içerir.

### <a name="better-dev-tools-for-c-and-net-and-hot-reload"></a>C++ ve .NET için daha iyi geliştirme araçları ve Çalışırken Yeniden Yükleme

[Visual Studio 2022 Preview 2,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/) daha iyi platformlar arası uygulama geliştirme araçları ve C++ derleme araçlarının en son sürümünü içerir. Ayrıca, uygulamanız **çalışırken C++ Çalışırken Yeniden Yükleme** .NET projelerini düzenleyebilirsiniz. Daha fazla bilgi için Visual Studio [**2022'de .NET**](https://devblogs.microsoft.com/visualstudio/speed-up-your-dotnet-and-cplusplus-development-with-hot-reload-in-visual-studio-2022/) ve C++ geliştirmenizi Çalışırken Yeniden Yükleme için bkz.

### <a name="updates-for-blazor--razor-editors--hot-reload-for-aspnet"></a>Blazor & Razor düzenleyicileri + Çalışırken Yeniden Yükleme güncelleştirmeleri ASP.NET

[Visual Studio 2022 Preview 4'te](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)yeni olan Blazor ve Razor düzenleyicileri için büyük bir güncelleştirme  ve bir dosyayı kaydeden veya CSS dosyalarına değişiklikleri canlı olarak uygulayan Çalışırken Yeniden Yükleme dahil olmak üzere ASP.NET Core'de Çalışırken Yeniden Yükleme için yeni özellikler &mdash; var! 

:::image type="content" source="media/vs-2022/hot-reload-blazor-css-live.gif" alt-text="Razor Çalışırken Yeniden Yükleme Blazor uygulamalarına ve CSS dosyalarına yönelik canlı yayın animasyonu.":::

## <a name="innovation-at-your-fingertips"></a>İnovasyon elinizin altında

Gerçek zamanlı & zaman uyumsuz işbirliği araçlarından günlük iş akışınız ile sorunsuz bir şekilde tümleştirilen gelişmiş içgörüler ve üretkenlik araçlarına kadar, Visual Studio 2022'de bu ve daha fazlası vardır.

### <a name="multi-repo-support-with-git-in-the-ide"></a>IDE'de Git ile çoklu depo desteği

Farklı Git depoları üzerinde barındırılan projelerle çalıştıysanız, dış araçları veya birden çok Visual Studio örneğini kullanarak bağlanabilirsiniz. Visual Studio [2022 Preview 3'den](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)başlayarak, birden çok depoda projeleri olan tek bir çözümle çalışarak tek bir örnekle katkıda Visual Studio. Daha fazla bilgi edinmek için [**bkz. Çoklu Visual Studio**](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) blog gönderisi.

### <a name="intellicode-improvements"></a>IntelliCode geliştirmeleri

* **Tam satır tamamlama:** Visual Studio 2022'de [IntelliCode](/visualstudio/intellicode/) özelliği artık kodu tek bir satıra kadar otomatik olarak tamamlar. Ayrıntılar için Bkz. [**Daha az tür, IntelliCode tamamlamaları ile daha fazla kod yazma**](https://devblogs.microsoft.com/visualstudio/type-less-code-more-with-intellicode-completions/) blog gönderisi.

* **Hızlı Eylemler** önerileri: [Visual Studio 2022 Preview 4'te](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)yeni olan IntelliCode artık ortak bir görev [](quick-actions.md)gerçekleştirdiğiniz zamanları tespit ediyor ve doğru Hızlı Eylem'i önererek yazarken tamamlanıyor. Daha fazla bilgi edinmek için IntelliCode ile sık kullanılan görevler için hızlı eylemleri keşfetme blog [**gönderisi'ne**](https://devblogs.microsoft.com/visualstudio/discover-quick-action-intellicode/) bakın.

## <a name="designing-for-everyone"></a>Herkes için tasarlama

Akışınızı daha iyi bir şekilde tutmak için kullanıcı arabirimini yenilebilirsiniz. Değişikliklerden bazıları, kullanıcı arabirimini modernleştiren veya kitleyi azaltan hafif görünüme sahip dokunmalardır.

### <a name="personalization-improvements"></a>Kişiselleştirme geliştirmeleri

En önemli odak alanlarından biri, IDE'Visual Studio daha kişiselleştirilmiş ve esnek hale getirir. Örneğin, [Visual Studio 2022 Preview 3,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/) temanız ile eşitleme Windows sunar. Bu nedenle burada "gece ışığı" özelliğini etkinleştirdiysek Visual Studio de kullanır. Daha fazla bilgi için Visual Studio [**2022**](https://devblogs.microsoft.com/visualstudio/personalize-your-visual-studio-2022/) blog gönderinize bakın.

## <a name="whats-next"></a>Sırada ne var?

2022'de planlamamız gerekenler hakkında daha fazla Visual Studio ister misiniz? Ayrıntılar için [**Yol Haritası**](/visualstudio/productinfo/vs-roadmap/) sayfasına ve [**Visual Studio 2022 vizyon**](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/) blog gönderisi sayfasına bakın.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Neden Visual Studio ekibine geri bildirim gönderebilirsiniz? Çünkü müşteri geri bildirimlerini ciddiye alıyoruz. Bu, yapacaklarının büyük bir fazlasını yapar.

* Bu özelliği nasıl geliştirebiliriz konusunda bir öneride Visual Studio, Özellik Öneri aracını [kullanarak bunu yapabiliriz.](suggest-a-feature.md)

* Sorun Bildirme aracını kullanarak Visual Studio, kilitlenmeler veya diğer performans sorunlarının yanıt vermeme durumuyla ilgili bir sorunla karşı karşımıza çıkarsanız, yeniden verme adımlarını ve destek dosyalarını bizimle [kolayca paylaşabilirsiniz.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2022 Preview 4](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)
* [Visual Studio 2022 Preview 3](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)
* [Visual Studio 2022 Preview 2](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/)
* [Visual Studio 2022 Preview 1](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)
* [Visual Studio 2022 vizyon](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)
