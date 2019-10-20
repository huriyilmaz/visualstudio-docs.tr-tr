---
title: Evrensel Windows Platformu için uygulama geliştirme (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ed601f6b3bfeba4d7aebed5955b340fb28908c74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660203"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP) için uygulama geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Evrensel Windows Platformu ve tek bir Windows çekirdeğiyle aynı uygulamayı telefonlardan masaüstü bilgisayarlardan herhangi bir Windows 10 cihazında çalıştırabilirsiniz. Bu Evrensel Windows uygulamalarını Visual Studio 2015 ve Evrensel Windows uygulama geliştirme araçları ile oluşturun.

 ![Evrensel Windows Platformu](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Uygulamanızı bir Windows 10 Phone, Windows 10 Masaüstü veya Xbox üzerinde çalıştırın. Aynı uygulama paketidir! Windows 10 tek ve birleştirilmiş çekirdeği kullanıma sunulmasıyla birlikte, tek bir uygulama paketi tüm platformlarda çalıştırılabilir. Birkaç platformda, platforma özgü davranışlardan yararlanmak üzere uygulamanıza ekleyebileceğiniz Uzantı SDK 'Ları vardır. Örneğin, mobil için bir uzantı SDK 'Sı, bir Windows Phone 'a basıldığında geri düğmesini işler. Projenizde bir uzantı SDK 'sına başvurdıysanız, bu SDK 'nın o platformda kullanılabilir olup olmadığını test etmek için yalnızca çalışma zamanı denetimleri ekleyin. Her platform için aynı uygulama paketine sahip olabilirsiniz!

 **Windows çekirdeği nedir?**

 İlk kez Windows 10 ' un tüm Windows 10 platformlarındaki ortak bir çekirdeğe sahip olması yeniden düzenlenmiş. Tek bir ortak kaynak, bir ortak Windows çekirdeği, bir dosya g/ç yığını ve bir uygulama modeli vardır. Kullanıcı arabirimi için yalnızca bir XAML kullanıcı arabirimi çerçevesi ve bir HTML UI çerçevesi vardır. Böylece uygulamanızın farklı Windows 10 cihazlarında çalışmasını kolaylaştıran harika bir uygulama oluşturmaya odaklanabilirsiniz.

 **Evrensel Windows Platformu tam olarak nedir?**

 Bu, yalnızca bir sözleşme ve sürüm koleksiyonudur. Bu, uygulamanızın çalıştırılacağı yeri hedeflemesini sağlar. Artık bir işletim sistemini hedeflemiyor. Şimdi uygulamanızı bir veya daha fazla cihaz ailesinden hedefleyebilirsiniz. Bu [Platform kılavuzundaki](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx)ayrıntılar hakkında daha fazla bilgi edinin.

## <a name="requirements"></a>Gereksinimler
 Evrensel Windows uygulama geliştirme araçları, uygulamanızın farklı cihazlarda nasıl göründüğünü görmek için kullanabileceğiniz öykünücülerle gelir. Bu öykünücüleri kullanmak istiyorsanız, bu yazılımı bir fiziksel makineye yüklemeniz gerekir. Fiziksel makinenin Windows 8.1 (x64) Professional sürümü veya üstünü çalıştırması ve Istemci Hyper-V ve Ikinci düzey adres çevirisi 'ni (SLAT) destekleyen bir işlemcisi olması gerekir. Sanal makineye Visual Studio yüklendiğinde Öykünücüler kullanılamaz.

 İhtiyacınız olan yazılımın listesi aşağıda verilmiştir:

- [Windows 10](http://windows.microsoft.com/windows/downloads)

- [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Evrensel Windows uygulaması geliştirme araçlarının isteğe bağlı özellikler listesinden seçildiğinden emin olun. Bu araçlar olmadan evrensel uygulamalarınızı oluşturmayacağız.

  Bu yazılımı yükledikten sonra, [Windows 10 cihazınızı](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) geliştirme için etkinleştirmeniz gerekir. (Artık her Windows 10 cihazı için bir geliştirici lisansına ihtiyacınız yoktur.)

  **Windows 8.1 ve Windows 7 desteği**

  Windows 10 dışındaki bir platformda, Visual Studio 2015 ile Evrensel Windows uygulamaları geliştirmeyi tercih ederseniz bunlar kısıtlamalardır:

- Windows 8.1: uygulamayı yerel olarak çalıştıramazsınız (yalnızca uzak bir Windows 10 cihazında). Öykünücüleri Visual Studio 'da kullanabilirsiniz, ancak benzeticiyi değildir.

- Windows 7: uygulamayı yerel olarak çalıştıramazsınız (yalnızca uzak bir Windows 10 cihazında). Visual Studio 'da öykünücüleri veya benzeticiyi kullanamazsınız.

  XAML tasarımcısını yalnızca geliştirme platformunuzun Windows 10 olması durumunda kullanabilirsiniz.

## <a name="universal-windows-apps"></a>Evrensel Windows uygulamaları
 C# [Windows 10 cihazları Için bir Evrensel Windows uygulaması oluşturmak](https://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10)üzere, Visual Basic C++ veya JavaScript 'ten tercih ettiğiniz geliştirme dilini seçin. Ya da [Bu Başlarken videosunu](http://channel9.msdn.com/Series/ConnectOn-Demand/229)izleyin.

 Mevcut Windows Mağazası 8,1 uygulamalarınız varsa Windows Phone 8,1 uygulamaları veya Visual Studio 2015 RC ile oluşturulmuş Evrensel Windows uygulamaları varsa, [Bu mevcut uygulamaların](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) en son Evrensel Windows platformu kullanması için bağlantı noktası oluşturabilirsiniz.

 Evrensel Windows uygulamanızı oluşturduktan sonra uygulamanızı bir Windows 10 cihazına yüklemek veya Windows Mağazası 'na göndermek için [paketlemeyi](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) yapmanız gerekir.
