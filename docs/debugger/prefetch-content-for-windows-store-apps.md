---
title: UWP uygulamaları içinde önceden 400000000000000000000000 |00000000000000000000 Microsoft Docs
description: UWP uygulamanıza daha hızlı yanıt veren bir uygulama yapmak için ContentPrefetcher'i kullanarak web Windows önceden bir istekte bulundurabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 60ec12f554c900aac74f63f463f4ea2c8276b66a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105203"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Önceden Visual Studio'de önceden ele içeriği kullanarak UWP uygulamalarının Visual Studio

 UWP uygulamanıza daha hızlı yanıt vermenizi Windows web sayfaları veya görüntüler gibi bazı web içeriğini [uygulamanın WinINet](/windows/desktop/WinInet/about-wininet) önbelleğine önceden yüklemesini sebilirsiniz. Bu işleve önceden geri ödeme denir. Özellikle başlangıçta kullanılan içerikler için etkilidir ancak sık kullanılan diğer içerikleri de önceden hazırlar. Yönteminin [Windows. Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) sınıfı, önceden yüklemek istediğiniz içeriğin URL'lerini belirtmenize izin verir. Uygulamanıza ContentPrefetcher [işlevselliği eklemeye](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) yönelik örnekler için Windows SDK İçerik önceden kullanım öncesi örneğine bakın.

 Windows, önceden ne zaman ve ne zaman indirileceklerini ve hangi kaynakların indirileceklerini belirlemek için heuristics kullanır. Bu çalışmalarda sistem ağı ve güç koşulları, kullanıcı uygulaması kullanım geçmişi ve önceki ön alma girişimlerinin sonuçları dikkate alınmıştır. Visual Studio'de Trigger Windows Store **App Prefetch** komutunu kullanarak Windows'i ContentPrefetcher heuristics'i yoksaymak ve belirtilen web içeriğinin hepsini önceden yüklemek için zorlarsiniz. Uygulamanın davranışını veya performansını bilinen bir durumda (yüklü veya yüklenmemiş) önceden yüklenecek içerikle test etmek için bu yararlı olabilir.

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher tarafından belirtilen kaynakların önceden yüklerini zorla yüklemek için
 Bu yordamda, ContentPrefetcher işlevselliğini zaten ayarlamış ve uygulama projenize önceden yüklenecek içerik URL'lerini belirttiğiniz varsaydır. Belirtilen kaynaklar yeni veya değiştirilmiş olduğunda içeriği önceden yüklemeye zorlamak için, Mağaza Uygulaması Ön Yükleme komutunu tetiklemeden önce uygulamayı **başlatmanız ve Windows durdurmanız** gerekir. URL'leri kaydetmek için önce uygulamayı çalıştırın. **Store Windows Ön Yükleme** komutunu tetikle ve ardından ContentPrefetcher'ı içeriği indirmeye ve önbelleğe eklemeye iter. Uygulamanın sonraki çalıştırmalarında içeriğin önceden yükleniyor olduğunu varsayabilirsiniz.

1. İçerik URL'lerini uygulamaya kaydetmek için uygulamayı başlatma. Hata Ayıklama **menüsünde Hata Ayıklamayı** Başlat **(Klavye kısayolu:** F5) öğesini seçin.

2. Hata Ayıklama **menüsünde Hata Ayıklamayı** Durdur **(Klavye kısayolu:** Shift + F5) öğesini seçin.

3. Hata Ayıklama **menüsünde Diğer Hata** Ayıklama **Hedefleri'ne** tıklayın ve ardından Mağaza Uygulaması **Ön Windows Tetikle'yi seçin.**

   Artık önceden alınan web kaynaklarıyla uygulamanıza hata ayıklama, test etme veya analiz etme.

> [!NOTE]
> Belirtilen web içeriğini her ekler veya değiştirirken bu adımları yineler.

## <a name="see-also"></a>Ayrıca bkz.
- [Blog gönderisi: Windows Store Uygulamaları için Visual Studio 2013 Tetikleme Güncelleştirme 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)