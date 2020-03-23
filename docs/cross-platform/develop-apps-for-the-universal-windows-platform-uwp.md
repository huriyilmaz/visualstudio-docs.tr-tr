---
title: Evrensel Windows Platformu (UWP) için uygulama geliştirme
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 2ef09f58d22e3cb72af5b745f16b2acf8920900e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75587153"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP) için uygulama geliştirme

Evrensel Windows Platformu ve tek Windows çekirdeğimizle, aynı uygulamayı telefonlardan masaüstü bilgisayarlara kadar tüm Windows 10 aygıtlarında çalıştırabilirsiniz. Visual Studio ve Universal Windows App geliştirme araçlarıyla bu Evrensel Windows uygulamalarını oluşturun.

![Evrensel Windows Platformu](../cross-platform/media/uwp_coreextensions.png)

Uygulamanızı Bir Windows 10 telefonunda, Windows 10 masaüstünde veya Xbox'ta çalıştırın. Aynı uygulama paketi! Windows 10 tekli, birleşik çekirdek tanıtımı ile, bir uygulama paketi tüm platformlarda çalıştırabilirsiniz. Çeşitli platformlarda, platforma özgü davranışlardan yararlanmak için uygulamanıza ekleyebileceğiniz uzantılı SDK'lar vardır. Örneğin, mobil cihazlar için bir uzantı SDK, Windows telefonunda basıldığında ki arka düğmeye işlenir. Projenizde bir uzantı SDK'ya başvurursanız, o sdk'nın bu platformda kullanılabilir olup olmadığını test etmek için çalışma zamanı denetimleri eklemeniz gereken bir süre eklemeniz gerekiyor. Bu şekilde her platform için aynı uygulama paketine sahip olabilirsiniz!

**Windows çekirdeği nedir?**

İlk defa, Windows tüm Windows 10 platformlarında ortak bir çekirdek olması için yeniden düzenlemektedir. Ortak bir kaynak, bir ortak Windows çekirdeği, bir dosya G/Ç yığını ve bir uygulama modeli vardır. UI için, sadece bir XAML Ara Birimi çerçevesi ve bir HTML UI çerçevesi vardır. Uygulamanızın farklı Windows 10 cihazlarında çalıştırMasını kolaylaştırdığımız için harika bir uygulama oluşturmaya odaklanabilirsiniz.

**Evrensel Windows Platformu tam olarak nedir?**

Evrensel Windows Platformu sadece sözleşmeler ve sürümler topluluğudur. Bunlar, uygulamanızın çalıştırabileceği yeri hedeflemenize olanak sağlar. Artık bir işletim sistemini hedeflemedin; şimdi bir veya daha fazla cihaz ailelerini hedefa savuruyorsunuz. [Evrensel Windows Platformu'na Giriş'i](/windows/uwp/get-started/universal-application-platform-guide)okuyarak daha fazla ayrıntı edinin.

## <a name="requirements"></a>Gereksinimler

Evrensel Windows Uygulaması geliştirme araçları, uygulamanızın farklı cihazlarda nasıl göründüğünü görmek için kullanabileceğiniz emülatörlerle birlikte gelir. Bu emülatörleri kullanmak istiyorsanız, bu yazılımı fiziksel bir makineye yüklemeniz gerekir. Fiziksel makine Windows 8.1 (x64) Professional sürümü veya daha yüksek çalıştırmak ve Istemci Hyper-V ve İkinci Düzey Adres Çeviri (SLAT) destekleyen bir işlemci olması gerekir. Visual Studio sanal bir makineye yüklendiğinde emülatörler kullanılamaz.

İhtiyacınız olan yazılımların listesi aşağıda veda edilebistir:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017, UWP geliştirmeyi yalnızca Windows 10'da destekler. Daha fazla bilgi için Visual Studio [Platform hedefleme](/visualstudio/productinfo/vs2017-compatibility-vs) ve [Sistem gereksinimlerine](/visualstudio/productinfo/vs2017-system-requirements-vs)bakın.

- [Görsel Stüdyo](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). İsteğe bağlı Evrensel Windows Platformu geliştirme iş yükünü de ihtiyacınız olacaktır.

     ![UWP iş yükü](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019, UWP geliştirmeyi yalnızca Windows 10'da destekler. Daha fazla bilgi için Visual Studio [Platform hedefleme](/visualstudio/releases/2019/compatibility/) ve [Sistem gereksinimlerine](/visualstudio/releases/2019/system-requirements/)bakın.

- [Görsel Stüdyo](https://visualstudio.microsoft.com/downloads). İsteğe bağlı Evrensel Windows Platformu geliştirme iş yükünü de ihtiyacınız olacaktır.

     ![UWP iş yükü](media/uwp_workload.png)

::: moniker-end

Bu yazılımı yükledikten sonra, geliştirme için Windows 10 aygıtınızı etkinleştirmeniz gerekir. Bkz. [Geliştirme için cihazınızı etkinleştirin.](/windows/uwp/get-started/enable-your-device-for-development) Artık her Windows 10 aygıtı için geliştirici lisansına ihtiyacınız yoktur.

## <a name="universal-windows-apps"></a>Evrensel Windows uygulamaları

Windows 10 aygıtları için Evrensel Windows Platformu uygulaması oluşturmak için C#, Visual Basic, C++ veya JavaScript'ten tercih ettiğiniz geliştirme dilini seçin. [İlk uygulamanızı oluşturun'u](/windows/uwp/get-started/your-first-app) okuyun veya Windows [10 Genel Bakış](https://channel9.msdn.com/Series/ConnectOn-Demand/229) videosunu izleyin.

Visual Studio 2015 ile oluşturulmuş mevcut Windows Mağazası 8.1 uygulamalarınız, Windows Phone 8.1 uygulamalarınız veya Evrensel Windows uygulamalarınız varsa, en son Evrensel Windows Platform'u kullanmak için bu uygulamaları bağlantı noktasına taşımanız gerekir. Bkz. [Windows Runtime 8.x'ten UWP'ye taşı.](/windows/uwp/porting/w8x-to-uwp-root)

Evrensel Windows uygulamanızı oluşturduktan sonra, uygulamanızı bir Windows 10 cihazına yüklemek veya Windows Mağazası'na göndermek için paketi niz gerekir. [Bkz. Ambalaj uygulamaları.](/windows/uwp/packaging/index)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da platform ötesi mobil geliştirme](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
