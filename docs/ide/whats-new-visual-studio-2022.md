---
title: Visual Studio 2022 ' deki yenilikler
titleSuffix: ''
description: Visual Studio 2022 ' nin önizleme sürümündeki yeni özellikler hakkında bilgi edinin.
ms.date: 11/08/2021
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
ms.openlocfilehash: ba5d202809bf6bb7b5587406332902842f30440a
ms.sourcegitcommit: ac681e983f3b217c3fd9d2a31e3a3ddcc4dd3546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "132041926"
---
# <a name="whats-new-in-visual-studio-2022"></a>Visual Studio 2022 ' deki yenilikler

**17,0 GA (genel kullanılabilirlik) sürümü için güncelleştirildi.** Bkz. [tam sürüm notları](/visualstudio/releases/2022/release-notes) | [Ürün yol haritasını](/visualstudio/productinfo/vs-roadmap/) görüntüle

>[!div class="button"]
>[2022 Visual Studio indirin](https://visualstudio.microsoft.com/downloads/)

[Visual Studio 2022](https://visualstudio.microsoft.com/vs/)ile her zaman geliştirici, herhangi bir uygulama ve herhangi bir platform için sunulan en iyi sınıf araçları ve hizmetleri elde edersiniz. Visual Studio ilk kez mi kullanıyorsunuz, yoksa yıllarca mi kullanıyorsunuz, en yeni sürümümüzü beğendiniz!

> [!TIP]
> [YouTube kanalımızda](https://www.youtube.com/visualstudio) [**Visual Studio 2022 başlatma olayına**](https://www.youtube.com/watch?v=f8jXO946eDw) göz atın. Ayrıca, [Twitch kanalımızda](https://www.twitch.tv/visualstudio)de yakalayabilirsiniz.

## <a name="performance-improvements"></a>Performans geliştirmeleri

Visual Studio 2022 daha hızlıdır, daha ulaşılabilir, daha hafif ve hem öğrenenlere hem de endüstriyel ölçek çözümleri oluşturmak için tasarlanmıştır.

### <a name="visual-studio-2022-is-64-bit"></a>Visual Studio 2022, 64 bit

Windows Visual Studio 2022 artık 64 bit bir uygulamadır. Bu, bellek tükenmeden en büyük ve en karmaşık çözümlerin bile açabilme, düzenleyebileceği, çalışabileceği ve hata ayıklamanıza yol açabilir. daha fazla bilgi edinmek için [Visual Studio 2022 vision](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/) ve [Visual Studio 2022 Preview 1](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/) blog gönderilerine bakın.

### <a name="find-in-files-is-faster"></a>Dosyalarda bul daha hızlıdır

[Visual Studio 2022 Preview 4](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)' te, bazı önemli özelliklerin performansını geliştirmeye odaklandık. Örneğin, [Orchard Core](https://github.com/OrchardCMS/OrchardCore)gibi büyük çözümleri ararken [dosyalarda bul](find-in-files.md) işlemi artık 3x daha hızlıdır.

:::image type="content" source="media/vs-2022/find-files-faster.gif" alt-text="Büyük bir C# çözümünü önceki Visual Studio sürümünün üç katı daha hızlı aradığı için dosyaları Bul özelliğinin animasyonu.":::

## <a name="build-modern-apps"></a>Modern uygulamalar oluşturun

Visual Studio 2022, Azure ile modern, bulut tabanlı uygulamalar oluşturmayı hızlı ve kolay hale getirir. ayrıca, yeni sürümümüzde hem Windows hem de Mac geliştiricileri için web, istemci ve mobil uygulamalar için .net 6 ve birleşik çerçevesi için tam destek bulunur. Visual Studio 2022, c++ iş yükünün yeni üretkenlik özellikleri, c++ 20 araçları ve ıntellisense ile güçlü desteğini içerir.

### <a name="better-dev-tools-for-c-and-net-and-hot-reload"></a>C++ ve .NET için daha iyi geliştirme araçları ve dinamik yeniden yükleme

[Visual Studio 2022 Preview 2](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/) , c++ 20 desteği dahil olmak üzere daha iyi platformlar arası uygulama geliştirme araçları ve c++ derleme araçlarının en son sürümünü içerir. Ayrıca, uygulamanızın çalışırken C++ veya .NET projelerini düzenleyebilmeniz için, **sık yeniden yükleme** güncelleştiriyoruz. daha fazla bilgi için, Visual Studio 2022 blog gönderisine [**.net ve C++ geliştirmenin etkin yeniden yükleme ile nasıl hızlanmasına**](https://devblogs.microsoft.com/visualstudio/speed-up-your-dotnet-and-cplusplus-development-with-hot-reload-in-visual-studio-2022/) bakın.

### <a name="updates-for-blazor--razor-editors--hot-reload-for-aspnet"></a>Blazor & Razor düzenleyicileri + ASP.NET için sık erişimli yeniden yükleme güncelleştirmeleri

[Visual Studio 2022 Preview 4](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)' te de yenidir, Blazor ve Razor düzenleyicilerle ilgili büyük bir güncelleştirme ve  &mdash; bir dosyayı kaydettiğinizde ya da CSS dosyalarına değişiklikler uyguladığınızda dinamik **yeniden** yükleme de dahil olmak üzere ASP.NET Core dinamik yeniden yüklemeye yönelik yeni yetenekler vardır!

:::image type="content" source="media/vs-2022/hot-reload-blazor-css-live.gif" alt-text="Razor ve Blazor uygulamalarında etkin yeniden yükleme animasyonu ve CSS dosyaları canlı.":::

## <a name="innovation-at-your-fingertips"></a>Yenilikçi yenilik

gerçek zamanlı & zaman uyumsuz işbirliği araçlarından, günlük iş akışınız ile sorunsuz bir şekilde tümleştirilen öngörüler ve üretkenlik araçlarına Visual Studio 2022, bu ve daha fazlasını içerir.

### <a name="multi-repo-support-with-git-in-the-ide"></a>IDE 'de git ile çoklu depo desteği

farklı Git depoları üzerinde barındırılan projelerle çalıştıysanız, bunlara bağlanmak için dış araçları veya Visual Studio birden çok örneğini kullanmış olabilirsiniz. [Visual Studio 2022 Preview 3](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)' ten itibaren, birden çok depodaki projelere sahip tek bir çözümle çalışabilir ve bu tek bir Visual Studio tek bir örneğinden bunlara katkıda bulunabilirsiniz. daha fazla bilgi edinmek için [**Visual Studio**](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) blog gönderisine bakın.

### <a name="intellicode-improvements"></a>Intellicode geliştirmeleri

* **tüm satır tamamlama**: Visual Studio 2022 ' de, [ıntellicode](/visualstudio/intellicode/) özelliği artık tek seferde tüm satıra kadar kodu otomatik olarak tamamlayabilir. Ayrıntılar için bkz. [**tür daha az, daha fazla kod, ıntellicode tamamiyle**](https://devblogs.microsoft.com/visualstudio/type-less-code-more-with-intellicode-completions/) tamamlandı blog gönderisi.

* **hızlı eylemler önerileri**: [Visual Studio 2022 Preview 4](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)' te yenidir, ıntellicode artık ortak bir görev gerçekleştirirken ve doğru [hızlı eylemi](quick-actions.md)önerdiğiniz zaman, yazarken hemen tamamlandığınızda bir nokta alabilir. Daha fazla bilgi edinmek için, [**ıntellicode blog gönderisine sahip yazarken sık kullanılan görevlere yönelik hızlı eylemleri bulma**](https://devblogs.microsoft.com/visualstudio/discover-quick-action-intellicode/) bölümüne bakın.

## <a name="designing-for-everyone"></a>Herkes için tasarlama

Akışınızı daha iyi tutmak için Kullanıcı arabirimini yenileiyoruz. Bazı değişiklikler, Kullanıcı arabirimini modernleştirin veya kalabonun azalmasını sağlayan hafif yüzeysel dokunmaktır.

### <a name="look--feel"></a>& göz atın

yeni ıonografınızdan hafif renkli kontrast oranı ayarlamalarına ve yeni bir [basamaklı dia kodu](https://github.com/microsoft/cascadia-code#welcome) yazı tipine, Visual Studio 2022 ' i herkes için daha erişilebilir hale getirmek için çalışıyoruz. tüm ayrıntılar için, Visual Studio 2022 blog gönderisine [**kullanıcı arabirimini yükselttik**](https://devblogs.microsoft.com/visualstudio/weve-upgraded-the-ui-in-visual-studio-2022/) .

:::image type="content" source="media/vs-2022/icon-refresh.png" alt-text="Visual Studio önceki ve yenilenen simgeler arasındaki karşıtlığın ekran görüntüsü.":::

### <a name="personalization"></a>Kişiselleştirme

anahtar odak alanlarımızdan biri, ıde 'yi kendi kendinize yapabilmeniz için Visual Studio daha kişiselleştirilmiş ve esnek hale getirme. örneğin, [Visual Studio 2022 Preview 3](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/) , Windows temanızla eşitleme olanağı sunar. bu nedenle, burada "gece ışığı" özelliğini etkinleştirdiyseniz Visual Studio de onu kullanır. daha fazla bilgi için [**Visual Studio 2022**](https://devblogs.microsoft.com/visualstudio/personalize-your-visual-studio-2022/) web günlüğü gönderisini kişiselleştirme bölümüne bakın.

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 2022 planlaması yaptığımız hakkında daha fazla bilgi edinmek mi istiyorsunuz? ayrıntılar için bkz. [**yol haritası**](/visualstudio/productinfo/vs-roadmap/) sayfası ve [**Visual Studio 2022 Preview**](/visualstudio/releases/2022/release-notes-preview/) sürüm notları.

## <a name="give-us-feedback"></a>Geri bildirimde bulunun

Visual Studio ekibine neden geri bildirim gönderilsin? Müşteri geri bildirimlerine önem veriyoruz. Yaptığımız kadar çok şey vardır.

* Visual Studio nasıl geliştirebileceğimizi gösteren bir öneride bulunmak isterseniz, [özellik öner](suggest-a-feature.md) aracını kullanarak bunu yapabilirsiniz.

* Visual Studio yanıt vermeyi, kilitlenmeleri veya diğer performans sorunlarını durdurduğu bir sorunla karşılaşırsanız, [sorun bildir](how-to-report-a-problem-with-visual-studio.md) aracını kullanarak yeniden üretme adımlarını ve destekleyici dosyaları bizimle paylaşabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2022 artık kullanılabilir](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-now-available/)
* [başlatma: Visual Studio 2022 GA (genel kullanılabilirlik)](https://devblogs.microsoft.com/visualstudio/join-us-november-8th-for-the-launch-of-visual-studio-2022/)
* [Visual Studio 2022 RC (sürüm adayı)](https://devblogs.microsoft.com/visualstudio/join-us-november-8th-for-the-launch-of-visual-studio-2022/)
* [Visual Studio 2022 Preview 4](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-4-is-now-available/)
* [Visual Studio 2022 Preview 3](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-3-now-available/)
* [Visual Studio 2022 Preview 2](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-2-is-out/)
* [Visual Studio 2022 Preview 1](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)
* [Visual Studio 2022 vizyonu](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)