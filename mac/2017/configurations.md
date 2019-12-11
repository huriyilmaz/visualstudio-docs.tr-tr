---
title: Yapı Yapılandırmalarını Anlama
description: Bu makalede Mac için Visual Studio içindeki çeşitli derleme konfigürasyonları açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983588"
---
# <a name="understanding-build-configurations"></a>Derleme yapılandırmasını anlama

## <a name="project-build-configurations"></a>Proje Derleme yapılandırması

Projeler birden fazla yapılandırmaya sahip olma eğilimindedir ve bunlar arasında geçiş yapmak, derleme zamanında farklı çıkışlar için izin verir. Örneğin, hata ayıklama yapılandırmasında hata ayıklama sembolleri çıkış yapılır ve hata ayıklayıcının, kilitlenen uygulamanın yığın izlemesinde işlev adlarını, parametreleri veya değişkenleri çözümlemesine izin verir. Bu ek bilgiler geliştirme sırasında yararlı olsa da, bir dosya boyutuna yol açar ve dağıtım için ideal değildir.

Her platformun derlemesi için belirli bir yapılandırması vardır.

## <a name="solution-configurations"></a>Çözüm yapılandırması

Proje yapılandırmalarına oturum, çözüm yapılandırması projenin tamamına yönelik özel yapılandırma oluşturmak için kullanılır. **Yapı > yapılandırmaları** öğesi altındaki **yapılandırma eşlemeleri** sekmesini kullanarak, aşağıdaki görüntüde gösterildiği gibi her çözüm öğesi için bir hedef yapılandırma atayabilirsiniz:

![Yapılandırma eşleme seçenekleri](media/projects-and-solutions-image3.png)

Yapılandırma hakkında daha fazla bilgi için, James Montemagno [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) videosunu inceleyin.

## <a name="run-configuration"></a>Çalıştırma yapılandırma

Önceki Xamarin Studio sürümlerinde, bir projeyi, genel Run/Debug komutu kullanılırken çalıştırılan/hata ayıklanan proje olan **Başlangıç projesi**olarak ayarlama seçeneğini belirleyebilirsiniz. Bu, Proje panelindeki projenin adı için kalın yazı tipiyle belirtilmiştir.

Mac için Visual Studio, bir başlangıç projesi ayarlamak yerine, _çalıştırma yapılandırması_ayarlayabilirsiniz. Çalışma yapılandırmaları, aşağıda gösterildiği gibi, derleme yapılandırma seçicisinin yanında bulunan bir açılan listede görüntülenir:

![Yapılandırma açılan, Çalıştır](media/projects-and-solutions-image8.png)

Çalıştırma yapılandırması, farklı amaçlar için bir projede tanımlanan bir ad ve birkaç yapılandırmaya sahip bir yürütme seçenekleri kümesidir. Çalışma yapılandırmalarının proje düzeyinde tanımlanması ve her yürütülebilir proje için varsayılan olarak otomatik olarak oluşturulur, ancak gerektiğinde bu kadar çok sayıda eklenebilir. Belirli proje türleri otomatik olarak ek çalışma yapılandırması oluşturur. Örneğin, watchOS projeleri bir _bakışta ve bildirim yapılandırması oluşturabilir._

Yapılandırma diğer geliştiricilerle paylaşılabilir (Bu durumda, yapılandırmaların. csproj dosyasında depolanması) veya yerel olarak saklanır (Bu durumda, bir. User dosyasında depolanacak).

### <a name="android-run-configurations"></a>Android çalıştırma yapılandırması

Android projeleri için çalıştırma yapılandırması, projeyi çalıştırırken veya hata ayıklarken hangi etkinlik, hizmet veya yayın alıcısının çalıştırılacağını belirtmenizi sağlar. Farklı başlatma koşullarında bileşenlerinizi test etmek için, amaç ek verileri geçirebilir ve amaç bayraklarını ayarlayabilirsiniz.

`MainLauncher` dışındaki etkinliklerin, bir fiziksel cihazda hata ayıklama için etkinlik özniteliğine `Exported=true` eklenmesi veya tanımlanmış amaç filtreleri olması gerekir.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Çalışma yapılandırmalarına dahil olabilecek verilerin örnekleri

Aşağıdaki listede, çalışma yapılandırmalarına eklenebilecek bazı veri örnekleri verilmiştir:

* Normal .NET projesi
  * Alternatif başlangıç uygulaması
  * Başlangıç bağımsız değişkenleri
  * Çalışma dizini
  * Ortam değişkenleri
  * Mono çalışma zamanı seçenekleri (yalnızca mono üzerinde çalışırken kullanılmak üzere)
* Android projesi
  * Giriş noktası (etkinlik, hizmet, alıcı)
  * Amaç bağımsız değişkenleri ve verileri
* iOS projesi
  * Mod (normal, arka plan getirme)
* iOS uzantı projesi
  * Başlangıç uygulaması: varsayılan veya özel
* WatchKit projesi
  * Mod (bakış, bildirim)
  * Bildirim yükü

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmasını anlama (Windows üzerinde Visual Studio)](/visualstudio/ide/understanding-build-configurations)
