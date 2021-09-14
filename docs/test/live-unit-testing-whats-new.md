---
title: Visual Studio 2017'de Live Unit Testing'daki YeniLer
description: Bu makalede, Live Unit Testing 2017 sürüm 15.3'Visual Studio sürümünden itibaren Visual Studio sürümüne eklenen yeni özellikler açıklanmıştır.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ae1caef04c1ccd1c51c38ddef5dc8c783bdbfaa9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628094"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Visual Studio 2017 için Live Unit Testing'daki yeniler

Bu konuda, Visual Studio 2017 sürüm 15.3'Live Unit Testing her Visual Studio sürümüne eklenen yeni özellikler listelenmiştir. Uygulama kullanımına genel bir bakış Live Unit Testing [bkz. Live Unit Testing ile Visual Studio.](live-unit-testing.md)

## <a name="version-154"></a>Sürüm 15.4

2017 Visual Studio 15.4 sürümünden itibaren, Live Unit Testing çeşitli alanlarda geliştirmeler ve iyileştirmeler içerir:

- **Geliştirilmiş keşfedebilirlik.** Live Unit Testing özelliğinin mevcut olduğunu bilemeyen kullanıcılar için Visual Studio IDE' de kullanıcı birim testleri içeren bir çözüm açtığında ancak etkinleştirilmemişse Live Unit Testing'den söz eden altın Live Unit Testing gösterir. Altın çubukta sunulan bilgiler, kullanıcının bu bilgiler hakkında daha fazla bilgi Live Unit Testing ve etkinleştirmeye olanak sağlar. Altın çubuk ayrıca önkoşullara Live Unit Testing bilgileri görüntüler. Bu modüller şunlardır:

  - Test bağdaştırıcıları eksik.
  - Test bağdaştırıcılarının eski sürümleri mevcuttur.
  - Çözüm tarafından NuGet paketlerin geri yüklemesi gerekir.

- **Görev Merkezi bildirimleriyle tümleştirme.** IDE Visual Studio artık, Live Unit Testing etkinleştirildiğinde neler olduğunu kolayca anlamaları için Görev Merkezi'nde bir arka plan işleme bildirimi Live Unit Testing gösterir. Bu, büyük bir çözümde Live Unit Testing başlatmayla ilgili temel sorunu çözen bir sorundur. Daha önce, kapsam simgeleri görünene kadar birkaç dakika için, kullanıcılar Live Unit Testing etkin olup olmadığını ve çalışıp çalışma olmadığını belirleyemedi. Artık değil!

- **MSTest framework** sürüm 1 desteği: Live Unit Testing üç popüler birim testi çerçevesiyle çalışır: xUnit, NUnit ve MSTest. Daha önce Live Unit Testing MSTest birim testi projelerinde MS Test sürüm 2 kullanılırken çalışıyordu. 2017 Visual Studio 15.4 sürümünden başlayarak, artık MSTest sürüm 1'i de destekliyor.

- **Güvenilirlik & Performansı:** Live Unit Testing, artık projelerin tam olarak yüklenmesini tamamlamış değilken sistemin daha iyi algılaması ve projelerin kilitlenmesini Live Unit Testing. Derleme performansı geliştirmeleri, sistem proje dosyasında hiçbir şeyin değişmediğini MSBuild projelerinin yeniden değerlendirilmesini de önlemektedir.

- **Çeşitli kullanıcı arabirimi iyileştirmeleri:** Sağ tıklama hareketinde bulunan kafa karıştırıcı Canlı Test Kümesi **– Dahil/Dışla** seçeneği, **Ekle/Dışla Live Unit Testing olarak yeniden adlandırıldı.** Test **komutu** menüsündeki   >  **Temizlemeyi sıfırla Live Unit Testing** seçeneği kaldırıldı. Artık Araçlar Seçenekler'i seçerek **ve**  >  **kalıcı**  >  **Live Unit Testing** **Sil'i seçerek erişilebilir.**

## <a name="version-153"></a>Sürüm 15.3

2017 Visual Studio 15.3 sürümünden başlayarak, Live Unit Testing iki ana alanda özellik geliştirmeleri ve geliştirmeleri sağlar:

- .NET Core ve .NET Standard. .NET Core Live Unit Testing C# veya .NET Standard yazılmış çözümlerde Visual Basic.

- Performans geliştirmeleri. İlk tam derlemeden ve test çalıştırmadan sonra performansın önemli ölçüde daha hızlı olduğunu fark Live Unit Testing. Ayrıca sonraki başlangıçlarda aynı çözümde önemli Live Unit Testing performans geliştirmesi olduğunu fark başlayacaktır. Artık veriler tarafından oluşturulan verileri Live Unit Testing ve güncel denetimlerle mümkün olduğunca yeniden kullanacağız.

Bu önemli eklemelere ek olarak Live Unit Testing geliştirmeleri de içerir:

- Artık test yöntemini normal yöntemlerden ayırmak için yeni bir beaker simgesi kullanılıyor. Boş bir beaker simgesi, belirli bir testin belirli bir teste dahil Live Unit Testing.

- Bir Live Unit Testing kapsamı simgesinin açılır kullanıcı arabirimi penceresinden bir test yöntemine tıklarken, artık kullanıcı arabirimi penceresinden ve kod düzenleyicisinden ayrılmak zorunda kalmadan testin hata ayıklaması için bu bağlamdan hata ayıklama seçeneğiniz vardır. Bu özellikle başarısız bir teste bakarak yararlı olur.

- Araçlar/Seçenekler/Genel'e birkaç ek yapılandırılabilir Live Unit Testing eklendi. Bellek için kullanılan belleği Live Unit Testing. Açık çözümünüz için kalıcı veri Live Unit Testing yolunu da belirtebilirsiniz.

- Test/Test menü çubuğunun altına birkaç ek menü öğesi Live Unit Testing. **Sıfırla** Temiz, kalıcı verileri siler ve yeniden üretir. **Seçenek** Araçlar/Seçenekler/Live Unit Testing/Genel'e atlar.

- Artık hedefli test yöntemlerinin kaynak kodda dışlamak istediğiniz kaynak kodunda belirtmek için aşağıdaki öznitelikleri Live Unit Testing:

  - xUnit için: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - NUnit için: `[Category("SkipWhenLiveUnitTesting")]`
  - MSTest için: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Birim Testine Giriş](live-unit-testing-intro.md)
- [Live Unit Testing ile Visual Studio](live-unit-testing.md)
