---
title: Yapı Yapılandırmalarını Anlama
description: Bu makalede, Mac için Visual Studio çeşitli yapı yapılandırmaları açıklanır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983588"
---
# <a name="understanding-build-configurations"></a>Yapı yapılandırmalarını anlama

## <a name="project-build-configurations"></a>Proje oluşturma yapılandırmaları

Projeler birden çok yapılandırmaya sahip olma eğilimindedir ve bunlar arasında geçiş yapı zamanında farklı çıktılar sağlar. Örneğin, hata ayıklama yapılandırması hata ayıklama simgeleri çıkararak hata ayıklayıcının çatlayan bir uygulamanın yığın izinden işlev adlarını, parametreleri veya değişkenleri çözmesine olanak sağlar. Bu ek bilgiler geliştirme sırasında yararlı olsa da, şişirilmiş bir dosya boyutuna yol açar ve dağıtım için ideal değildir.

Her platform, kendi yapısı için özel yapılandırmalara sahiptir.

## <a name="solution-configurations"></a>Çözüm yapılandırmaları

Proje yapılandırmalarına benzer şekilde, çözüm yapılandırmaları tüm proje için özel yapılandırmalar oluşturmak için kullanılır. **Yapı > Yapılandırmaları** öğesinin altındaki Yapılandırma **Eşlemeleri** sekmesini kullanarak, aşağıdaki resimde gösterildiği gibi her çözüm öğesi için bir hedef yapılandırma atayabilirsiniz:

![Yapılandırma Eşleme Seçenekleri](media/projects-and-solutions-image3.png)

Yapılandırmalar hakkında daha fazla bilgi için James Montemagno'nun [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) videosuna bakın.

## <a name="run-configuration"></a>Yapılandırmayı çalıştır

Xamarin Studio'nun önceki sürümlerinde, bir projeyi, genel çalıştırma/hata ayıklama komutunu kullanırken çalıştırılan/debutladı olan **Başlangıç Projesi**olarak ayarlama seçeneğini seçebilirsiniz. Bu, proje defterinde projenin adı için cesur bir yazı tipi ile belirtilmiştir.

Mac için Visual Studio'da, başlangıç projesi ayarlamak _yerine, çalıştıran yapılandırmayı_ayarlayabilirsiniz. Çalıştırma yapılandırmaları, araç çubuğunda, aşağıda gösterildiği gibi yapı yapılandırma seçicisinin yanında açılır listede sunulur:

![Yapılandırma açılır düşüşünü çalıştırma](media/projects-and-solutions-image8.png)

Çalıştırılan yapılandırma, bir ada ve projede farklı amaçlariçin tanımlanan çeşitli yapılandırmalara sahip yürütme seçenekleri kümesidir. Çalıştır yapılandırmaları proje düzeyinde tanımlanır ve her yürütülebilir proje için otomatik olarak bir varsayılan oluşturulur, ancak gerektiği kadar eklemek mümkündür. Belirli proje türleri otomatik olarak ek çalıştırma yapılandırmaları oluşturur. Örneğin, watchOS projeleri _Bakış ve Bildirim yapılandırmaları oluşturabilir._

Yapılandırmalar diğer geliştiricilerle paylaşılabilir (bu durumda yapılandırmalar .csproj dosyasında depolanabilir) veya yerel olarak tutulabilir (bu durumda bir .user dosyasında depolanırlar).

### <a name="android-run-configurations"></a>Android çalıştır yapılandırmaları

Android projeleri için yapılandırmaları çalıştırın, projeyi çalıştırırken veya hata ayıklarken hangi etkinlik, hizmet veya yayın alıcısının başlatılacağınızda belirtebilirsiniz. Farklı başlatma koşullarında bileşenlerinizi test edebilmek için kasıtlı ek verileri geçirebilir ve niyet bayraklarını ayarlayabilirsiniz.

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
