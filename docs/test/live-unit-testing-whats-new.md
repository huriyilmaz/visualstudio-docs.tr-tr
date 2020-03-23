---
title: Visual Studio 2017 Canlı Ünite Testinde Yenilikler
titleSuffix: ''
ms.date: 10/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
- Live Unit Testing What's New
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 7f7ab0c257bfed4521e95d9da12eaa0b9e25a71e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114278"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Visual Studio 2017 Canlı Ünite Testinde Yenilikler

Bu konu Visual Studio 2017 sürüm 15.3 ile başlayan Visual Studio'nun her sürümünde Canlı Birim Testine eklenen yeni özellikleri listeler. Canlı Birim Testi'nin nasıl kullanılacağına genel bir bakış için [Visual Studio ile Canlı Birim Testi'ne](live-unit-testing.md)bakın.

## <a name="version-154"></a>Sürüm 15.4

Visual Studio 2017 sürüm 15.4 ile başlayan Canlı Birim Testi, bazı alanlarda iyileştirmeler ve geliştirmeler içerir:

- **Geliştirilmiş keşfedilebilirlik**. Canlı Birim Testi özelliğinin var olduğunu bilmeyen kullanıcılar için Visual Studio IDE, kullanıcı birim testleri içeren bir çözüm açtığında Canlı Birim Testi'nden bahseden bir altın çubuk gösterir, ancak Canlı Birim Testi etkinleştirilmez. Altın çubukta sunulan bilgiler, kullanıcının Canlı Birim Testi hakkında daha fazla bilgi edinmesini ve bunu etkinleştirmesini sağlar. Altın çubuk, Canlı Birim Testi ön koşulları karşılanmadığında da bilgileri görüntüler. Bunlar:

  - Test bağdaştırıcıları eksik.
  - Test bağdaştırıcılarının eski sürümleri mevcuttur.
  - Çözüm tarafından başvurulan NuGet paketlerinin geri yüklenmesi gereklidir.

- **Görev Merkezi bildirimleri ile tümleştirme.** Visual Studio IDE artık Görev Merkezi'nde Bir Canlı Birim Testi arka plan işleme bildirimi gösterir, böylece kullanıcılar Canlı Birim Testi etkinleştirildiğinde neler olduğunu kolayca anlayabilirler. Bu, büyük bir çözüm üzerinde Canlı Birim Testi başlatma nın temel sorununu giderer. Daha önce, kapsama simgeleri ortaya çıkana kadar birkaç dakika boyunca, kullanıcılar Canlı Birim Testi'nin gerçekten etkin olup olmadığını ve çalışıp çalışmadığını belirleyemediler. Artık değil!

- **MSTest framework version 1 desteği**: Canlı Birim Testi zaten üç popüler birim test çerçevesi ile çalışır: xUnit, NUnit ve MSTest. Daha önce, Canlı Birim Testi yalnızca MSTest birim test projeleri MS Test sürüm 2 kullanıldığında işe yaralsA. Visual Studio 2017 sürüm 15.4 ile başlayarak, şimdi de MSTest sürüm 1'i de destekliyor.

- **Güvenilirlik & Performansı**: Canlı Birim Testi artık projelerin tam olarak yüklenmeyi tamamlamadığını daha iyi algılamasını sağlar ve Canlı Birim Testi'nin çökmesini önler. Yapı performansı iyileştirmeleri, sistem proje dosyasındaki hiçbir şeyin değişmediğini bildiğinde MSBuild projelerinin yeniden değerlendirilmesini de önler.

- **Çeşitli kullanıcı arabirimi iyileştirmeleri**: Kafa karıştırıcı Canlı Test Seti – Sağ tıklama hareketinden **Ekle/Hariç tutma** **seçeneği, Canlı Birim Test Ekle/Hariç Tut**olarak yeniden adlandırıldı.  >  **Canlı**Ünite Test menüsündeki Temiz**Test'i** **Sıfırla** seçeneği kaldırıldı. Artık **Araçlar** > **Seçenekleri** > **Canlı Birim Testi'ni** seçerek ve Kalıcı Verileri **Sil'i**seçerek erişilebilir.

## <a name="version-153"></a>Sürüm 15.3

Visual Studio 2017 sürüm 15.3 ile başlayan Live Unit Test, iki ana alanda iyileştirmeler ve geliştirmeler sunar:

- .NET Core ve .NET Standard desteği. C# veya Visual Basic ile yazılmış .NET Core ve .NET Standart çözümlerinde Canlı Birim Testi'ni kullanabilirsiniz.

- Performans geliştirmeleri. Canlı Birim Testi altında yapılan ilk tam test ve çalıştırmadan sonra performansın önemli ölçüde daha hızlı olduğunu fark edeceksiniz. Aynı çözüm üzerinde Canlı Birim Testi'nin sonraki başlangıcında da önemli performans artışı fark edeceksiniz. Artık Live Unit Testing tarafından oluşturulan verileri sürdürüyoruz ve güncel kontrollerle mümkün olduğunca yeniden kullanıyoruz.

Bu önemli eklemelere ek olarak, Canlı Birim Testi aşağıdaki geliştirmeleri içerir:

- Yeni bir beher simgesi artık bir test yöntemini normal yöntemlerden ayırt etmek için kullanılır. Boş bir beher simgesi, belirli bir testin Canlı Birim Testi'ne dahil olmadığını gösterir.

- Canlı Birim Test kapsamı simgesinin açılır ara birimi penceresinden bir test yöntemini tıklattığınızda, artık testin hatasını ui penceresindeki ve kod düzenleyicisinden ayrılmadan bu bağlamdan ayıklama seçeneğiniz vardır. Bu, özellikle başarısız bir teste baktığınızda kullanışlıdır.

- Araçlar/Seçenekler/Canlı Birim Testi/Genel'e birkaç ek yapılandırılabilir seçenek eklendi. Canlı Birim Testi için kullanılan belleği kapatabilirsiniz. Ayrıca, açık çözümünüz için kalıcı Canlı Birim Testi verilerinin dosya yolunu da belirtebilirsiniz.

- Test/Canlı Birim Testi'nin menü çubuğunun altına birkaç ek menü öğesi eklendi. **Temiz'i Sıfırla,** kalıcı verileri siler ve yeniden oluşturur. **Seçenekler** Araçlar/Seçenekler/Canlı Birim Testi/Genel'e atlar.

- Artık, Hedeflenen test yöntemlerini Canlı Birim Testi'nden hariç tutmak istediğiniz kaynak kodunda belirtmek için aşağıdaki öznitelikleri kullanabilirsiniz:

  - xUnit için:`[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - NUnit için:`[Category("SkipWhenLiveUnitTesting")]`
  - MSTest için:`[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Birim Testine Giriş](live-unit-testing-intro.md)
- [Visual Studio ile Canlı Ünite Testi](live-unit-testing.md)
