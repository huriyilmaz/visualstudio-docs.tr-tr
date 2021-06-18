---
title: Evrensel Windows Platformu (UWP) için uygulama geliştirme
description: Visual Studio ve Evrensel Windows Platformu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: e54fdd71d848d1edad93fe38598d71c9dbbede7f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308122"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP) için uygulama geliştirme

Evrensel Windows Platformu ve tek Windows çekirdeğimiz ile aynı uygulamayı telefonlardan masaüstüne Windows 10 herhangi bir cihazda çalıştırabilirsiniz. Visual Studio ve Evrensel Windows Uygulaması geliştirme araçlarıyla bu Evrensel Windows uygulamalarını oluşturun.

![Evrensel Windows Platformu](../cross-platform/media/uwp_coreextensions.png)

Uygulamayı telefon, Windows 10 masaüstünde veya Xbox Windows 10 çalıştırın. Bu aynı uygulama paketidir! Tek ve birleşik Windows 10 ile tüm platformlarda tek bir uygulama paketi çalışır. Çeşitli platformlarda, platforma özgü davranışlardan yararlanmak için uygulamanıza ek olarak ekleyebilirsiniz uzantı SDK'leri vardır. Örneğin, mobil için uzantı SDK'sı, Windows phone'da basılmış olan geri düğmesini işler. Projeniz içinde bir uzantı SDK'sına başvurursanız, o SDK'nın o platformda kullanılabilir olup olduğunu test etmek için çalışma zamanı denetimleri eklemeniz gerekir. Her platform için aynı uygulama paketine sahip olmak için bu şekilde devam edin!

**Windows çekirdeği nedir?**

Windows ilk kez tüm platformlarda ortak bir çekirdek olacak şekilde yeniden Windows 10. Bir ortak kaynak, bir ortak Windows çekirdeği, bir dosya I/O yığını ve bir uygulama modeli vardır. Kullanıcı arabirimi için yalnızca bir XAML UI çerçevesi ve bir HTML UI çerçevesi vardır. Harika bir uygulama oluşturmaya odaklanabilirsiniz çünkü biz uygulamalarınızı farklı cihazlarda çalıştırmayı Windows 10.

**Tam olarak hangi Evrensel Windows Platformu?**

Bu Evrensel Windows Platformu, yalnızca anlaşmalardan ve sürümlerden bir koleksiyondur. Bunlar, uygulamanın nerede çalıştırılaylarını hedeflemenize olanak sağlar. Artık bir işletim sistemini hedeflemezsiniz; artık bir veya daha fazla cihaz ailelerini hedefleyebilirsiniz. [Evrensel Windows Platformu'a giriş'i okuyarak daha fazla ayrıntı Evrensel Windows Platformu.](/windows/uwp/get-started/universal-application-platform-guide)

## <a name="requirements"></a>Gereksinimler

Evrensel Windows Uygulaması geliştirme araçları, uygulamanın farklı cihazlarda nasıl göründüğünü görmek için kullanabileceğiniz öykünücülerle birlikte gelir. Bu öykünücüleri kullanmak için bu yazılımı fiziksel bir makineye yüklemeniz gerekir. Fiziksel makinenin Windows 8.1 (x64) Professional sürümünü veya daha yüksek bir sürümünü çalıştırması ve İstemci Hyper-V ile İkinci Düzey Adres Çevirisi (SLAT) destekleyen bir işlemcisi olması gerekir. Öykünücüler, sanal Visual Studio makineye yüklenirken kullanılamaz.

İşte ihtiyacınız olan yazılımların listesi:

::: moniker range="vs-2017"

- [Windows 10.](https://support.microsoft.com/help/17777/downloads-for-windows) Visual Studio 2017, UWP geliştirmeyi yalnızca Windows 10. Diğer ayrıntılar için bkz. Visual Studio [Platform hedefleme ve](/visualstudio/productinfo/vs2017-compatibility-vs) Sistem [gereksinimleri.](/visualstudio/productinfo/vs2017-system-requirements-vs)

- [Visual Studio.](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Ayrıca isteğe bağlı geliştirme Evrensel Windows Platformu gerekir.

     ![UWP iş yükü](media/uwp_workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

- [Windows 10.](https://support.microsoft.com/help/17777/downloads-for-windows) Visual Studio 2019, UWP geliştirmeyi yalnızca Windows 10. Diğer ayrıntılar için bkz. Visual Studio [Platform hedefleme ve](/visualstudio/releases/2019/compatibility/) Sistem [gereksinimleri.](/visualstudio/releases/2019/system-requirements/)

- [Visual Studio.](https://visualstudio.microsoft.com/downloads) Ayrıca isteğe bağlı geliştirme Evrensel Windows Platformu gerekir.

     ![UWP iş yükü](media/uwp_workload.png)

::: moniker-end

Bu yazılımı yükledikten sonra, geliştirme için Windows 10 etkinleştirmeniz gerekir. Bkz. [Cihazınızı geliştirme için etkinleştirme.](/windows/uwp/get-started/enable-your-device-for-development) Artık her bir cihaz için geliştirici lisansına Windows 10 gerekir.

## <a name="universal-windows-apps"></a>Evrensel Windows uygulamaları

C#, Visual Basic, C++ veya JavaScript'te tercih ettiğiniz geliştirme dilini seç Evrensel Windows Platformu cihazlar için bir Windows 10 oluşturun. İlk [uygulamanızı oluşturma makalenizi okuyun](/windows/uwp/get-started/your-first-app) veya Windows 10 [Için Araçlar videosunu](https://channel9.msdn.com/Series/ConnectOn-Demand/229) izleyin.

Mevcut Windows Mağazası 8.1 uygulamalarınız, Windows Phone 8.1 uygulamalarınız veya Visual Studio 2015 ile oluşturulmuş Evrensel Windows uygulamalarınız varsa, en son uygulamaları kullanmak için bu uygulamaları Evrensel Windows Platformu. Bkz. [Windows Çalışma Zamanı 8.x'den UWP'ye taşıma.](/windows/uwp/porting/w8x-to-uwp-root)

Evrensel Windows uygulamanızı oluşturduk sonra, bir uygulama cihazına yüklemek için Windows 10 veya Windows Mağazası'ya göndermeniz gerekir. Bkz. [Uygulamaları paketleme.](/windows/uwp/packaging/index)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de platformlar arası mobil Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
