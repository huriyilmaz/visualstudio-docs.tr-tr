---
title: Windows Mağazası uygulamaları için içeriği önceden getirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac6479b4dbb0815374174140deb0d660636ac9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300519"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Windows Mağazası uygulamaları için önceden getirilmiş içerikler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Windows Mağazası uygulamanızın daha hızlı yanıt vermesini sağlamak için, Windows 'u, Web sayfaları veya resimleri gibi bazı Web içeriklerini uygulamanın [Winınet](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[Wininet](https://msdn.microsoft.com/library/aa383630.aspx)önbelleğine önyükleyebilir. Bu işlevselliğe ön getirme denir. Başlangıçta kullanılan içerik için özellikle etkilidir, ancak sık kullanılan diğer içerikleri de önceden getirebilirsiniz. [Windows. Networking. BackgroundTransfer. ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) sınıfının yöntemleri, önyüklemek Istediğiniz Içeriğin URI 'lerini belirtmenize olanak tanır.  
  
 Windows, ön alma işleminin ne zaman ve ne zaman yapılacağını ve hangi kaynakların indirileceğini belirleyen buluşsal yöntemler kullanır. Buluşsal yöntemler, sistem ağ ve güç koşulları, Kullanıcı uygulaması kullanım geçmişi ve önceki önceden getirme girişimlerinin sonuçlarını alır. Visual Studio 'da, Windows **Mağazası uygulaması önceden getirme komutunu tetikleyip** Windows 'un ContentPrefetcher buluşsal yöntemlerini yoksaymasını ve belirtilen Web içeriğinin tümünün önyük iadesini sağlayabilirsiniz. Bu, uygulamanın davranışını veya performansını bilinen bir durumda (yüklenmiş veya yüklü değil) önceden ayarlanabilir içerikle test etmek istiyorsanız yararlı olabilir.  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher belirtilen kaynakları önceden yüklemeye zorlamak için  
 Bu yordamda, ContentPrefetcher işlevini önceden ayarlamış olduğunuzu ve içerik URI 'Lerini uygulama projenizde önyüklemeye belirttiğinizi varsaymış olursunuz. Belirtilen kaynaklar yeni veya değiştirildiğinde içeriği önceden yüklemeye zorlamak için, **Windows Mağazası uygulamasını zorla önceden getirme** komutunu seçmeden önce uygulamayı başlatıp durdurmanız gerekir. URI 'Leri kaydettirmek için önce uygulamayı çalıştırın. **Windows Mağazası uygulamasını önceden getirme komutunu tetikleyin** , sonra ContentPrefetcher içeriği indirmeye ve önbelleğe eklemeye zorlar. Uygulamanın sonraki çalıştırmalarından içeriğin önceden yüklenmiş olduğunu varsayabilirsiniz.  
  
1. Uygulamayı, önceden getirme içerik URI 'Lerini uygulamayla kaydetmek için başlatın. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' ı seçin (klavye kısayolu: F5).  
  
2. **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur** ' u seçin (klavye kısayolu: SHIFT + F5).  
  
3. **Hata** Ayıkla menüsünde, **diğer hata ayıklama hedefleri** ' ni seçin ve ardından **Windows Mağazası uygulamasını önceden getirme**' yi seçin.  
  
   Artık uygulamanızı önceden getirilen Web kaynaklarıyla ayıklayabilirsiniz, test edebilir veya çözümleyebilirsiniz.  
  
> [!NOTE]
> Belirtilen Web içeriğini her eklediğinizde veya değiştirdiğinizde bu adımları yineleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Blog gönderisi: Visual Studio 2013 güncelleştirme 2 ' de Windows Mağazası uygulamaları için önceden getirme tetikleniyor](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
