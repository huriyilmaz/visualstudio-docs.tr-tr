---
title: UWP uygulamalarında önceden getirilen içeriği kullanarak hata ayıklama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 65b889452a23bb970cbee4c65455679a3473abab
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348073"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Visual Studio 'da önceden getirilen içeriği kullanarak UWP uygulamalarında hata ayıklama

 UWP uygulamanızı daha hızlı hale getirmek için, Windows 'u, Web sayfaları veya resimler gibi bazı Web içeriklerini uygulamanın [Winınet](/windows/desktop/WinInet/about-wininet) önbelleğine yüklemek üzere isteyebilirsiniz. Bu işlevselliğe ön getirme denir. Başlangıçta kullanılan içerik için özellikle etkilidir, ancak sık kullanılan diğer içerikleri de önceden getirebilirsiniz. [Windows. Networking. BackgroundTransfer. ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) sınıfının yöntemleri, önyüklemek Istediğiniz Içeriğin URI 'lerini belirtmenize olanak tanır. Uygulamanıza ContentPrefetcher işlevselliği ekleme örnekleri için Windows SDK [içerik önceden getirme örneğine](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) bakın.

 Windows, ön alma işleminin ne zaman ve ne zaman yapılacağını ve hangi kaynakların indirileceğini belirleyen buluşsal yöntemler kullanır. Buluşsal yöntemler, sistem ağ ve güç koşulları, Kullanıcı uygulaması kullanım geçmişi ve önceki önceden getirme girişimlerinin sonuçlarını alır. Visual Studio 'da, Windows **Mağazası uygulaması önceden getirme komutunu tetikleyip** Windows 'un ContentPrefetcher buluşsal yöntemlerini yoksaymasını ve belirtilen Web içeriğinin tümünün önyük iadesini sağlayabilirsiniz. Bu, uygulamanın davranışını veya performansını bilinen bir durumda (yüklenmiş veya yüklü değil) önceden ayarlanabilir içerikle test etmek istiyorsanız yararlı olabilir.

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher belirtilen kaynakları önceden yüklemeye zorlamak için
 Bu yordamda, ContentPrefetcher işlevini önceden ayarlamış olduğunuzu ve içerik URI 'Lerini uygulama projenizde önyüklemeye belirttiğinizi varsaymış olursunuz. Belirtilen kaynaklar yeni veya değiştirildiğinde içeriği önceden yüklemeye zorlamak için, **Windows Mağazası uygulamasını zorla önceden getirme** komutunu seçmeden önce uygulamayı başlatıp durdurmanız gerekir. URI 'Leri kaydettirmek için önce uygulamayı çalıştırın. **Windows Mağazası uygulamasını önceden getirme komutunu tetikleyin** , sonra ContentPrefetcher içeriği indirmeye ve önbelleğe eklemeye zorlar. Uygulamanın sonraki çalıştırmalarından içeriğin önceden yüklenmiş olduğunu varsayabilirsiniz.

1. Uygulamayı, önceden getirme içerik URI 'Lerini uygulamayla kaydetmek için başlatın. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' ı seçin (klavye kısayolu: F5).

2. **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye kısayolu: SHIFT + F5).

3. **Hata** Ayıkla menüsünde, **diğer hata ayıklama hedefleri** ' ni seçin ve ardından **Windows Mağazası uygulamasını önceden getirme**' yi seçin.

   Artık uygulamanızı önceden getirilen Web kaynaklarıyla ayıklayabilirsiniz, test edebilir veya çözümleyebilirsiniz.

> [!NOTE]
> Belirtilen Web içeriğini her eklediğinizde veya değiştirdiğinizde bu adımları yineleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Blog gönderisi: Visual Studio 2013 güncelleştirme 2 ' de Windows Mağazası uygulamaları için önceden getirme tetikleniyor](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)