---
title: Visual Studio 2022'de yapılan yeniler
titleSuffix: ''
description: Visual Studio 2022'de yeni özellikler hakkında bilgi.
ms.date: 01/26/2022
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
ms.openlocfilehash: 3b5181f8cbc173a90146f38ecae1f22ff6bae76c
ms.sourcegitcommit: ebd651e00fe3bae5914c211c4828219bf7d1fc70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137798541"
---
# <a name="whats-new-in-visual-studio-2022"></a>Visual Studio 2022'de yapılan yeniler

**17.0 GA (Genel Kullanılabilirlik) sürümü için güncelleştirildi.** Tüm [sürüm notlarına bakın |](/visualstudio/releases/2022/release-notes) Ürün [yol haritasını görüntüleme](/visualstudio/productinfo/vs-roadmap/)

>[!div class="button"]
>[2022 Visual Studio indirme](https://visualstudio.microsoft.com/downloads/)

[2022](https://visualstudio.microsoft.com/vs/)Visual Studio ile her zaman herhangi bir geliştirici, herhangi bir uygulama ve herhangi bir platform için kullanılabilen sınıfının en iyisi araçlara ve hizmetlere sahip oluruz. İster ilk kez Visual Studio ister yıllardır kullanıyor olun, en yeni sürümde çok fazla şey var!

> [!TIP]
> YouTube [**kanalımızda Visual Studio 2022**](https://www.youtube.com/watch?v=f8jXO946eDw) başlatma [etkinliğine göz atabilirsiniz.](https://www.youtube.com/visualstudio) Bunu Kanal kanalımızda da [yakalayabilirsiniz.](https://www.twitch.tv/visualstudio)

## <a name="performance-improvements"></a>Performans geliştirmeleri

Visual Studio 2022 hem öğrenciler hem de endüstriyel ölçek çözümlerine sahip olanlar için tasarlanmıştır.

### <a name="visual-studio-2022-is-64-bit"></a>Visual Studio 2022 64 bittir

Visual Studio 2022 Windows artık 64 bitlik bir uygulamadır. Bu, belleğin yetersiz kalmadan en büyük ve en karmaşık çözümleri bile aç, düzenle, çalıştır ve hata ayıkla. Daha fazla bilgi edinmek için hem [Visual Studio 2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/) vision hem [de Visual Studio 2022 Preview 1](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/) blog gönderilerini okuyun.

### <a name="find-in-files-is-faster"></a>Dosyalarda Bul daha hızlı

[2022 Visual Studio de,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)birkaç önemli özelliğin performansını geliştirmeye odaklandı. Örneğin, [Dosyalarda Bul artık](find-in-files.md) Core gibi büyük çözümler aranırken 3 kat daha [hızlıdır.](https://github.com/OrchardCMS/OrchardCore)

:::image type="content" source="media/vs-2022/find-files-faster.gif" alt-text="Büyük bir C# çözümünde önceki sürümden üç kat daha hızlı arama yaptığı için Dosyalarda Bul özelliğinin animasyonu Visual Studio.":::

> [!NOTE]
> **17.1 Önizleme 3'te** yeni: Yeni dizinli arama özelliğiyle Dosyalarda Bul özelliği daha da hızlıdır! Daha fazla bilgi için [bkz. Visual Studio 2022'de](https://devblogs.microsoft.com/visualstudio/code-search-in-visual-studio-is-about-to-get-much-faster/) Kod araması çok daha hızlı bir blog gönderisi almak için.

## <a name="build-modern-apps"></a>Modern uygulamalar oluşturma

Visual Studio 2022, Azure ile modern, bulut tabanlı uygulamalar derlemeyi hızlı ve kolay bir şekilde sağlar. Ayrıca, yeni sürümde [.NET 6](https://devblogs.microsoft.com/dotnet/announcing-net-6/) için tam destek ve hem web, istemci hem de Mac geliştiricileri için web, istemci ve mobil uygulamalar için birleşik Windows vardır. Ayrıca Visual Studio 2022' de yeni üretkenlik özellikleri, C++20 aracı ve [IntelliSense](using-intellisense.md)ile C++ iş yükü için sağlam destek içerir.

### <a name="better-dev-tools-for-c-and-net-and-hot-reload"></a>C++ ve .NET için daha iyi geliştirme araçları ve Çalışırken Yeniden Yükleme

[Visual Studio 2022, C++20](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/) desteği eklemek için daha iyi platformlar arası uygulama geliştirme araçları ve en son C++ derleme araçları sürümünü içerir.

Ayrıca, uygulamanız **çalışırken C++ Çalışırken Yeniden Yükleme** .NET projelerini düzenleyebilirsiniz. Daha fazla bilgi için [**Visual Studio 2022**](https://devblogs.microsoft.com/visualstudio/speed-up-your-dotnet-and-cplusplus-development-with-hot-reload-in-visual-studio-2022/) blog gönderisinde Çalışırken Yeniden Yükleme ile .NET ve C++ geliştirmenizi hızlandırın ve [C#, C++](../debugger/hot-reload.md) veya Visual Basic Docs ile Visual Studio'da Çalışırken Yeniden Yükleme ile kod yazma ve hata ayıklama sayfasına bakın.

### <a name="updates-for-blazor--razor-editors--hot-reload-for-aspnet"></a>Blazor & Razor düzenleyicileri + Çalışırken Yeniden Yükleme güncelleştirmeleri ASP.NET

[Visual Studio 2022'](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/) de Blazor ve [Razor](https://devblogs.microsoft.com/visualstudio/introducing-the-new-razor-editor-in-visual-studio-2022/) düzenleyicileri için büyük bir güncelleştirmenin ve ASP.NET Core'de **Çalışırken Yeniden Yükleme** için bir dosyayı kaydeden veya CSS dosyalarına değişiklikleri canlı olarak uygulayan Çalışırken Yeniden Yükleme dahil olmak üzere yeni özellikler &mdash; içerir! 

:::image type="content" source="media/vs-2022/hot-reload-blazor-css-live.gif" alt-text="Razor Çalışırken Yeniden Yükleme Blazor uygulamalarına ve CSS dosyalarına yönelik canlı yayın animasyonu.":::

## <a name="innovation-at-your-fingertips"></a>İnovasyon elinizin altında

Gerçek zamanlı & zaman uyumsuz işbirliği araçlarından günlük iş akışınızla sorunsuz bir şekilde tümleştirilen gelişmiş içgörüler ve üretkenlik araçlarına kadar Visual Studio 2022'de bu ve daha fazlası vardır.

### <a name="multi-repo-support-with-git-in-the-ide"></a>IDE'de Git ile çoklu depo desteği

Farklı Git depoları üzerinde barındırılan projelerle çalıştıysanız, dış araçları veya birden çok Visual Studio örneğini kullanarak bağlanabilirsiniz. [2022 Visual Studio de,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)birden çok depoda projeleri olan tek bir çözümle çalışarak bunların tek bir örneğiyle katkıda Visual Studio. Daha fazla bilgi edinmek için [**bkz. Çoklu Visual Studio**](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) blog gönderisi.

> [!NOTE]
> **17.1 Önizleme 2'de** yeni: Git özellik kümesine daha fazla işlev eklemeye devam ediyoruz. En son bilgiler için [2022'de yeni Git özelliklerine Visual Studio](https://devblogs.microsoft.com/visualstudio/introducing-new-git-features-to-visual-studio-2022/) blog gönderisi'ne bakın.

### <a name="intellicode-improvements"></a>IntelliCode geliştirmeleri

* **Tam satır tamamlama:** Visual Studio 2022'de [IntelliCode](/visualstudio/intellicode/) özelliği artık kodu tek bir satıra kadar otomatik olarak tamamlar. Ayrıntılar için Bkz. [**Daha az tür, IntelliCode tamamlamaları ile daha fazla kod yazma**](https://devblogs.microsoft.com/visualstudio/type-less-code-more-with-intellicode-completions/) blog gönderisi.

* **Hızlı Eylemler** önerileri: [Visual Studio 2022'de](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)yeni olan IntelliCode artık ortak bir görev gerçekleştirdiğiniz [](quick-actions.md)zamanları tespit ediyor ve doğru Hızlı Eylem'i önererek yazarken tamamlanıyor. Daha fazla bilgi edinmek için IntelliCode ile sık kullanılan görevler için hızlı eylemleri keşfetme blog [**gönderisi'ne**](https://devblogs.microsoft.com/visualstudio/discover-quick-action-intellicode/) bakın.

## <a name="designing-for-everyone"></a>Herkes için tasarlama

Akışınızı daha iyi bir şekilde tutmak için kullanıcı arabirimini yenilebilirsiniz. Değişikliklerden bazıları, kullanıcı arabirimini modernleştiren veya kitleyi azaltan görünümel dokunmalar içerir.

### <a name="look--feel"></a>Nasıl & bakın

Yeni simgeografiden ince renk karşıtlığı oranı ayarlamaları ve yeni [bir Cascadia Code](https://github.com/microsoft/cascadia-code#welcome) yazı tipine kadar, 2022'de 2022'Visual Studio herkesin daha erişilebilir olmasını sağlamak için çalışıyoruz. Tüm ayrıntılar için Visual Studio [**2022**](https://devblogs.microsoft.com/visualstudio/weve-upgraded-the-ui-in-visual-studio-2022/) blog gönderisinde kullanıcı arabirimini yükselttik.

:::image type="content" source="media/vs-2022/icon-refresh.png" alt-text="Önceki ve yenilenmiş simgeler arasındaki karşıtlık ekran görüntüsü Visual Studio.":::

### <a name="personalization"></a>Kişiselleştirme

En önemli odak alanlarından biri, IDE'Visual Studio daha kişiselleştirilmiş ve esnek hale getirir. Örneğin, [Visual Studio 2022,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/) temanız ile eşitleme Windows sunar. Bu nedenle burada "gece ışığı" özelliğini etkinleştirdiysek Visual Studio de kullanır. Daha fazla bilgi için Visual Studio [**2022**](https://devblogs.microsoft.com/visualstudio/personalize-your-visual-studio-2022/) blog gönderinize bakın.

## <a name="whats-next"></a>Sırada ne var?

2022'de planlamamız gerekenler hakkında daha fazla Visual Studio ister misiniz? Ayrıntılar için [**Yol Haritası**](/visualstudio/productinfo/vs-roadmap/) sayfasına ve [**Visual Studio 2022 Preview**](/visualstudio/releases/2022/release-notes-preview/) sürüm notlarına bakın.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Neden Visual Studio ekibine geri bildirim gönderebilirsiniz? Çünkü müşteri geri bildirimlerini ciddiye alıyoruz. Bu, yapacaklarının büyük bir fazlasını yapar.

* Bu özelliği nasıl geliştirebiliriz konusunda bir öneride Visual Studio, Özellik Öneri aracını [kullanarak bunu yapabiliriz.](suggest-a-feature.md)

* Sorun Bildirme aracını kullanarak Visual Studio, kilitlenme veya diğer performans sorunlarının yanıt vermeme durumuyla ilgili bir sorunla karşı karşımıza çıkarsanız, yeniden verme adımlarını ve destek dosyalarını bizimle [kolayca paylaşabilirsiniz.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2022 artık kullanılabilir](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-now-available/)
* [Başlatma: Visual Studio 2022 GA (Genel Kullanılabilirlik)](https://devblogs.microsoft.com/visualstudio/join-us-november-8th-for-the-launch-of-visual-studio-2022/)
* [Visual Studio 2022 RC (Sürüm Adayı)](https://devblogs.microsoft.com/visualstudio/join-us-november-8th-for-the-launch-of-visual-studio-2022/)
* [Visual Studio 2022 Preview 4](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)
* [Visual Studio 2022 Preview 3](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)
* [Visual Studio 2022 Preview 2](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/)
* [Visual Studio 2022 Preview 1](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)
* [Visual Studio 2022 vizyon](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)