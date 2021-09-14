---
title: Evrensel Windows Platformu (UWP) için uygulama geliştirme
description: Visual Studio ve Evrensel Windows Platformu geliştirme araçlarını kullanarak uygulama oluşturma hakkında bilgi edinin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631670"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP) için uygulama geliştirme

Evrensel Windows Platformu ve tek Windows çekirdekle aynı uygulamayı, telefonlardan masaüstü bilgisayarlardan herhangi bir Windows 10 cihazda çalıştırabilirsiniz. bu evrensel Windows uygulamalarını Visual Studio ve evrensel Windows uygulama geliştirme araçlarıyla oluşturun.

![Evrensel Windows Platformu](../cross-platform/media/uwp_coreextensions.png)

uygulamanızı bir Windows 10 telefonda, Windows 10 masaüstünde veya Xbox 'ta çalıştırın. Aynı uygulama paketidir! tek bir birleştirilmiş çekirdek Windows 10 giriş ile, tek bir uygulama paketi tüm platformlarda çalıştırılabilir. Birkaç platformda, platforma özgü davranışlardan yararlanmak üzere uygulamanıza ekleyebileceğiniz Uzantı SDK 'Ları vardır. örneğin, mobil için bir uzantı SDK 'sı, Windows telefonda basılan geri düğmesini işler. Projenizde bir uzantı SDK 'sına başvurdıysanız, bu SDK 'nın o platformda kullanılabilir olup olmadığını test etmek için yalnızca çalışma zamanı denetimleri ekleyin. Her platform için aynı uygulama paketine sahip olabilirsiniz!

**Windows çekirdeği nedir?**

ilk kez, Windows tüm Windows 10 platformları genelinde ortak bir çekirdeğe sahip olmak için yeniden düzenlenmiş. tek bir ortak kaynak, bir ortak Windows çekirdeği, bir dosya g/ç yığını ve bir uygulama modeli vardır. Kullanıcı arabirimi için yalnızca bir XAML kullanıcı arabirimi çerçevesi ve bir HTML UI çerçevesi vardır. uygulamanızın farklı Windows 10 cihazlarda çalışmasını kolaylaştıran harika bir uygulama oluşturmaya odaklanabilirsiniz.

**Evrensel Windows Platformu tam olarak nedir?**

Evrensel Windows Platformu yalnızca sözleşmelerin ve sürümlerin bir koleksiyonudur. Bu, uygulamanızın çalıştırılacağı yeri hedeflemesini sağlar. Artık bir işletim sistemini hedeflemiyor; Artık bir veya daha fazla cihaz ailelerini hedefleyebilirsiniz. [Evrensel Windows Platformu girişi](/windows/uwp/get-started/universal-application-platform-guide)okuyarak daha fazla bilgi edinin.

## <a name="requirements"></a>Gereksinimler

evrensel Windows uygulama geliştirme araçları, uygulamanızın farklı cihazlarda nasıl göründüğünü görmek için kullanabileceğiniz öykünücülerle gelir. Bu öykünücüleri kullanmak istiyorsanız, bu yazılımı bir fiziksel makineye yüklemeniz gerekir. fiziksel makinenin Windows 8.1 (x64) Professional sürümünü veya üstünü çalıştırması ve Hyper-V İstemcisi ve ikinci düzey adres çevirisini (SLAT) destekleyen bir işlemcisi olması gerekir. bir sanal makineye Visual Studio yüklendiğinde öykünücüler kullanılamaz.

İhtiyacınız olan yazılımın listesi aşağıda verilmiştir:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017, yalnızca Windows 10 üzerinde UWP geliştirmeyi destekler. daha ayrıntılı bilgi için bkz. [Platform hedefleme](/visualstudio/productinfo/vs2017-compatibility-vs) ve [sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs)Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). ayrıca, isteğe bağlı Evrensel Windows Platformu geliştirme iş yüküne da ihtiyacınız olacaktır.

     ![UWP iş yükü](media/uwp_workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019, yalnızca Windows 10 üzerinde UWP geliştirmeyi destekler. daha ayrıntılı bilgi için bkz. [Platform hedefleme](/visualstudio/releases/2019/compatibility/) ve [sistem gereksinimleri](/visualstudio/releases/2019/system-requirements/)Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/downloads). ayrıca, isteğe bağlı Evrensel Windows Platformu geliştirme iş yüküne da ihtiyacınız olacaktır.

     ![UWP iş yükü](media/uwp_workload.png)

::: moniker-end

bu yazılımı yükledikten sonra, Windows 10 cihazınızı geliştirme için etkinleştirmeniz gerekir. Bkz. [cihazınızı geliştirme Için etkinleştirme](/windows/uwp/get-started/enable-your-device-for-development). her Windows 10 cihaz için artık bir geliştirici lisansına ihtiyacınız yoktur.

## <a name="universal-windows-apps"></a>Evrensel Windows uygulamaları

Windows 10 cihazlara yönelik bir Evrensel Windows Platformu uygulaması oluşturmak için C#, Visual Basic, C++ veya JavaScript 'te tercih ettiğiniz geliştirme dilini seçin. [ilk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app) konusunu okuyun veya [Windows 10 genel bakış videosu için araçları](https://channel9.msdn.com/Series/ConnectOn-Demand/229) izleyin.

Visual Studio 2015 ile oluşturulan Windows Store 8,1 uygulamaları, Windows Phone 8,1 uygulamaları veya evrensel Windows uygulamalar varsa, en son Evrensel Windows Platformu kullanmak için bu uygulamaların bağlantı noktası oluşturmanız gerekir. bkz. [Windows Çalışma Zamanı 8. x öğesinden UWP 'e taşıma](/windows/uwp/porting/w8x-to-uwp-root).

evrensel Windows uygulamanızı oluşturduktan sonra, uygulamanızı Windows 10 bir cihaza yüklemek veya Windows deposuna göndermek için paketlemeyi yapmanız gerekir. Bkz. [paketleme uygulamaları](/windows/uwp/packaging/index).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio platformlar arası mobil geliştirme](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
