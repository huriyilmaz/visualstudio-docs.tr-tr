---
title: Visual Studio 2017 ' de Live Unit Testing yenilikler
titleSuffix: ''
ms.date: 10/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
- Live Unit Testing What's New
author: jillre
ms.author: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: b8a7627572daf872ddbd66a9c93f2c904246977d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653016"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Visual Studio 2017 için Live Unit Testing yenilikler

Bu konuda, Visual Studio 2017 sürüm 15,3 ' den başlayarak her Visual Studio sürümünde Live Unit Testing eklenen yeni özellikler listelenmiştir. Live Unit Testing kullanma hakkında genel bir bakış için bkz. [Visual Studio ile Live Unit Testing](live-unit-testing.md).

## <a name="version-154"></a>Sürüm 15,4

Visual Studio 2017 sürüm 15,4 ' den başlayarak, Live Unit Testing çeşitli alanlarda iyileştirmeler ve iyileştirmeler içerir:

- **İyileştirilmiş bulunabilirliği**. Live Unit Testing özelliğinin mevcut olduğunu bilemeyen kullanıcılar için, Visual Studio IDE, Kullanıcı birim testlerini içeren bir çözümü her açtığında Live Unit Testing bahsetmeyen bir altın çubuk gösterir, ancak Live Unit Testing etkinleştirilmez. Altın renkli çubukta sunulan bilgiler, kullanıcının Live Unit Testing hakkında daha fazla bilgi almasına ve etkinleştirmesini sağlar. Altın renkli çubuk, Live Unit Testing önkoşulları karşılanmazsa bilgileri de görüntüler. Bu güncelleştirmeler şunlardır:

  - Test bağdaştırıcıları eksik.
  - Test bağdaştırıcılarının eski sürümleri mevcuttur.
  - Çözüm tarafından başvurulan NuGet paketlerinin geri yüklenmesi gerekiyor.

- **Görev Merkezi bildirimleri Ile tümleştirme**. Visual Studio IDE artık, kullanıcıların Live Unit Testing etkinleştirildiğinde ne olduğunu kolayca anlayabilmesi için, görev merkezi 'nde Live Unit Testing bir arka plan işleme bildirimi gösterir. Bu, büyük bir çözümde Live Unit Testing başlatma ile ilgili önemli sorunu ele alır. Daha önce, kapsam simgeleri görünene kadar birkaç dakika boyunca, kullanıcılar Live Unit Testing gerçekten etkinleştirilip etkinleştirilmeyeceğini ve çalışıp çalışmadığını belirlemeiyordu. Artık değil!

- **MSTest Framework sürüm 1 Için destek**: Live Unit Testing zaten üç popüler birim test çerçevesiyle çalışmaktadır: xUnit, NUnit ve MSTest. Daha önce Live Unit Testing yalnızca MSTest birim testi projeleri MS test sürüm 2 ' i kullanırken kullanılabilir. Visual Studio 2017 sürüm 15,4 ' den itibaren artık MSTest sürüm 1 de desteklenir.

- **Güvenilirlik & performansı**: Live Unit Testing artık, projenin tamamen yüklemeyi tamamlamadıklarında ve kilitlenen Live Unit Testing kaçınarak sistemin daha iyi algılayabilmesini sağlar. Yapı performansı geliştirmeleri Ayrıca, sistem proje dosyasındaki hiçbir şeyin değiştiğini bildiğinde MSBuild projelerinin yeniden değerlendirilmesinden kaçının.

- **Çeşitli kullanıcı arabirimi işlevselliklerindeki**: sağ tıklama hareketinizden karışık **canlı test kümesi – dahil etme/hariç tutma** seçeneği **Live Unit Testing dahil etme/hariç tutma**olarak yeniden adlandırıldı. **Test**  > **Live Unit Testing** menüsündeki **temiz sıfırlama** seçeneği kaldırılmıştır. Artık **araçlar**  > **Seçenekler**  > **Live Unit Testing** ve **kalıcı verileri Sil**' i seçerek erişilebilir.

## <a name="version-153"></a>Sürüm 15,3

Visual Studio 2017 sürüm 15,3 ' den başlayarak, Özellikler ve iyileştirmeler iki ana alanda Live Unit Testing:

- .NET Core ve .NET Standard için destek. .NET Core üzerinde Live Unit Testing, C# veya Visual Basic yazılmış .NET Standard çözümleri kullanabilirsiniz.

- Performans geliştirmeleri. Live Unit Testing altında testlerin ilk tam derlemeden ve çalıştırıldıktan sonra performansın önemli ölçüde daha hızlı olduğunu fark edeceksiniz. Ayrıca, aynı çözümde Live Unit Testing sonraki başlangıçlarda önemli performans iyileştirmesini de fark edeceksiniz. Artık Live Unit Testing tarafından oluşturulan verileri kalıcı hale getiriyoruz ve güncel denetimler sayesinde mümkün olduğunca yeniden kullanıma sunduk.

Bu büyük eklemelere ek olarak, Live Unit Testing aşağıdaki geliştirmeleri içerir:

- Artık bir test yöntemini normal yöntemlerden ayırt etmek için yeni bir Beaker simgesi kullanılır. Boş bir Beaker simgesi, belirli bir testin Live Unit Testing dahil edilmediğini belirtir.

- Bir Live Unit Testing kapsam simgesinin açılır Kullanıcı arabirimi penceresinde bir test yöntemine tıkladığınızda, artık Kullanıcı arabirimi penceresinde bu bağlamdan test etme ve kod düzenleyicisinden çıkmak zorunda kalmadan hata ayıklama seçeneğiniz vardır. Bu, özellikle başarısız bir teste baktığınızda yararlı olur.

- Araçlar/Seçenekler/Live Unit Testing/genel 'e birkaç ek yapılandırılabilir seçenek eklenmiştir. Live Unit Testing için kullanılan belleği büyük bir şekilde kullanabilirsiniz. Ayrıca, açık çözümünüz için kalıcı Live Unit Testing verilerinin dosya yolunu da belirtebilirsiniz.

- Test/Live Unit Testing menü çubuğunun altına birkaç ek menü öğesi eklenmiştir. **Temiz sıfırlama** kalıcı verileri siler ve yeniden oluşturur. **Seçenek** , Araçlar/seçenekler/Live Unit Testing/genel ' i atlar.

- Artık Live Unit Testing ' den hedeflenen test yöntemlerini dışlamak istediğiniz kaynak kodu belirtmek için aşağıdaki öznitelikleri kullanabilirsiniz:

  - XUnit için: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - NUnit için: `[Category("SkipWhenLiveUnitTesting")]`
  - MSTest için: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Birim Testine Giriş](live-unit-testing-intro.md)
- [Visual Studio ile Live Unit Testing](live-unit-testing.md)
