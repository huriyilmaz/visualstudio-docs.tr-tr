---
title: Yapı Yapılandırmalarını Anlama
description: Bu makalede, Mac için Visual Studio çeşitli yapı yapılandırmaları açıklanır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128405"
---
# <a name="understanding-build-configurations"></a>Yapı yapılandırmalarını anlama

Geliştirme işlemi sırasında farklı türde yapılarda kullanmak üzere farklı çözüm ve proje özellikleri yapılandırmalarını depolayabilirsiniz. Visual Studio for Mac tarafından şablon kullanılarak oluşturulan projeler, genellikle bir uygulamanın hata ayıklama ve uygulamanın dağıtımını destekleyen Hata Ayıklama ve Sürüm yapılandırmalarını içerir. 

Özel yapılandırmalar oluşturmak istiyorsanız, yapı [yapılandırmaları oluşturma ve düzenleme'ye](/visualstudio/mac/create-and-edit-configurations)bakın.

>[!NOTE]
>Bu konu Mac için Visual Studio için geçerlidir. Windows'daki Visual Studio için [bkz.](/visualstudio/ide/understanding-build-configurations)

## <a name="solution-configurations"></a>Çözüm yapılandırmaları

Çözüm yapılandırmaları, bir çözümdeki tüm projeler için yapılandırmaları belirtmek için kullanılır. **Yapı > Yapılandırmaları** öğesinin altındaki Yapılandırma **Eşlemeleri** sekmesini kullanarak, açılan çözümdeki her öğe için bir hedef yapılandırma atayabilirsiniz. Bu, aşağıdaki resimde gösterilmiştir:

![Yapılandırma Eşleme Seçenekleri](media/projects-and-solutions-image3.png)

Yapılandırmalar hakkında daha fazla bilgi için James Montemagno'nun [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) videosuna bakın.

## <a name="project-build-configurations"></a>Proje oluşturma yapılandırmaları

Projeler birden çok yapılandırmaya sahip olma eğilimindedir. Proje hedeflerinin konfigürasyonu ve platformu, oluşturulduğunda kullanılacak özellikleri belirtmek için birlikte kullanılır. Yapılandırmalar arasında geçiş yapmak, yapı zamanında farklı çıktılara olanak tanır. Örneğin, hata ayıklama yapılandırması hata ayıklama simgeleri çıkararak hata ayıklayıcının çatlayan bir uygulamanın yığın izinden işlev adlarını, parametreleri veya değişkenleri çözmesine olanak sağlar. Bu ek bilgiler geliştirme sırasında yararlı olsa da, şişirilmiş bir dosya boyutuna yol açar ve dağıtım için ideal değildir.

Her platform, kendi yapısı için özel yapılandırmalara sahiptir. Projeler için yapı yapılandırma sayfalarına **Proje Seçenekleri** iletişim kutusundaki **Yapı** bölümüne gezinerek erişilebilir. Projeyi sağ tıklayarak ve **Seçenekler'i** seçerek veya çözüm gezgininde projeyi çift tıklatarak bu iletişim kutusunu açın.

## <a name="run-configuration"></a>Yapılandırmayı çalıştır

Mac için Visual Studio bir _çalışma yapılandırması_ayarlamanızı sağlar. Çalıştırma yapılandırmaları, araç çubuğunda, aşağıda gösterildiği gibi yapı yapılandırma seçicisinin yanında açılır listede sunulur:

![Yapılandırma açılır düşüşünü çalıştırma](media/projects-and-solutions-image8.png)

Çalıştırılan yapılandırma, bir ada ve projede farklı amaçlariçin tanımlanan çeşitli yapılandırmalara sahip yürütme seçenekleri kümesidir. Çalıştır yapılandırmaları proje düzeyinde tanımlanır ve her çalıştırılabilir proje için otomatik olarak bir varsayılan oluşturulur, ancak gerektiği kadar eklemek mümkündür. Belirli proje türleri otomatik olarak ek çalıştırma yapılandırmaları oluşturur. Örneğin, watchOS projeleri _Bakış ve Bildirim yapılandırmaları oluşturabilir._

Yapılandırmalar diğer geliştiricilerle paylaşılabilir (bu durumda yapılandırmalar .csproj dosyasında depolanabilir) veya yerel olarak tutulabilir (bu durumda bir .user dosyasında depolanırlar).

### <a name="android-run-configurations"></a>Android çalıştır yapılandırmaları

Android projeleri için yapılandırmaları çalıştırın, projeyi çalıştırırken veya hata ayıklarken belirli bir etkinliğin, hizmetin veya yayın alıcısının belirtimini başlatın. Farklı başlatma koşullarında bileşenlerinizi test etmek için kasıtlı ek veri geçirebilir ve niyet bayrakları ayarlayabilirsiniz.

Fiziksel bir `MainLauncher` aygıtta hata `Exported=true` ayıklamak için Etkinlik özniteliğine eklenen veya Niyet filtreleri tanımlanmış olması gerekir.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Çalıştırılan yapılandırmalara dahil edilebilen veri örnekleri

Aşağıdaki liste, çalıştırılan yapılandırmalara dahil edilebilen bazı veri örnekleri sağlar:

* Düzenli .NET projesi
  * Alternatif başlangıç uygulaması
  * Bağımsız değişkenleri başlat
  * Çalışma dizini
  * Ortam değişkenleri
  * Mono çalışma süresi seçenekleri (yalnızca Mono'da çalışırken kullanılacak)
* Android projesi
  * Giriş noktası (etkinlik, servis, alıcı)
  * Amaç bağımsız değişkenleri ve veriler
* iOS projesi
  * Mod (Normal, Arka Plan Getir)
* iOS genişletme projesi
  * Başlangıç uygulaması: varsayılan veya özel
* WatchKit projesi
  * Mod (Bakış, Bildirim)
  * Bildirim yükü

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı yapılandırmalarını anlama (Windows'ta Visual Studio)](/visualstudio/ide/understanding-build-configurations)
