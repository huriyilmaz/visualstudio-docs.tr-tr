---
title: Yapı Yapılandırmalarını Anlama
description: Bu makalede Mac için Visual Studio içindeki çeşitli derleme konfigürasyonları açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 911d8d3a65c414bc3c98494bda75c46b778e5b2b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584028"
---
# <a name="understanding-build-configurations"></a>Yapı yapılandırmalarını anlama

Geliştirme süreci sırasında farklı türlerde derlemelerde kullanmak üzere çözüm ve proje özelliklerinin farklı yapılandırmalarının depolanmasını sağlayabilirsiniz. Bir şablon kullanarak Mac için Visual Studio tarafından oluşturulan projeler genellikle, bir uygulamanın hata ayıklamasını ve uygulama dağıtımını destekleyen hata ayıklama ve sürüm yapılandırmalarının dahil edilir. 

Özel yapılandırma oluşturmak isterseniz, bkz. [yapı yapılandırması oluşturma ve bunları Düzenle](./create-and-edit-configurations.md).

>[!NOTE]
>Bu konu Mac için Visual Studio için geçerlidir. Windows üzerinde Visual Studio için bkz. [derleme yapılandırmasını anlama](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Çözüm yapılandırması

Çözüm konfigürasyonları, bir Çözümdeki tüm projelere yönelik konfigürasyonları belirtmek için kullanılır. **Yapı > yapılandırmaları** öğesi altındaki **yapılandırma eşlemeleri** sekmesini kullanarak, açılan çözümdeki her öğe için bir hedef yapılandırma atayabilirsiniz. Bu, aşağıdaki görüntüde gösterilmiştir:

![Yapılandırma eşleme seçenekleri](media/projects-and-solutions-image3.png)

Yapılandırma hakkında daha fazla bilgi için, James Montemagno [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) videosunu inceleyin.

## <a name="project-build-configurations"></a>Proje Derleme yapılandırması

Projeler birden fazla yapılandırmaya sahip olmaya eğilimlidir. Yapılandırma ve platform bir proje hedefleri, derlendiklerinde kullanılacak özellikleri belirtmek için birlikte kullanılır. Yapılandırma arasında geçiş yapmak, derleme zamanında farklı çıkışlar yapılmasına izin verir. Örneğin, hata ayıklama yapılandırmasında hata ayıklama sembolleri çıkış yapılır ve hata ayıklayıcının, kilitlenen uygulamanın yığın izlemesinde işlev adlarını, parametreleri veya değişkenleri çözümlemesine izin verir. Bu ek bilgiler geliştirme sırasında yararlı olsa da, bir dosya boyutuna yol açar ve dağıtım için ideal değildir.

Her platformun derlemesi için belirli bir yapılandırması vardır. Projeler için derleme yapılandırma sayfalarına, **Proje seçenekleri** Iletişim kutusunda **derleme** bölümüne gidilerek erişilebilir. Projeye sağ tıklayıp **Seçenekler** ' i seçerek veya Çözüm Gezgini ' nde projeye çift tıklayarak bu iletişim kutusunu açın.

## <a name="run-configuration"></a>Yapılandırmayı Çalıştır

Mac için Visual Studio, _çalıştırma yapılandırması_ayarlamanıza olanak sağlar. Çalışma yapılandırmaları, aşağıda gösterildiği gibi, derleme yapılandırma seçicisinin yanında bulunan bir açılan listede görüntülenir:

![Yapılandırma açılan, Çalıştır](media/projects-and-solutions-image8.png)

Çalıştırma yapılandırması, farklı amaçlar için bir projede tanımlanan bir ad ve birkaç yapılandırmaya sahip bir yürütme seçenekleri kümesidir. Çalışma yapılandırmalarının proje düzeyinde tanımlanması ve her yürütülebilir proje için varsayılan olarak otomatik olarak oluşturulması gerekir, ancak gereken sayıda ekleme yapılabilir. Belirli proje türleri otomatik olarak ek çalışma yapılandırması oluşturur. Örneğin, watchOS projeleri bir  _bakışta ve bildirim yapılandırması oluşturabilir._

Yapılandırma diğer geliştiricilerle paylaşılabilir (Bu durumda, yapılandırmaların. csproj dosyasında depolanması) veya yerel olarak saklanır (Bu durumda, bir. User dosyasında depolanacak).

### <a name="android-run-configurations"></a>Android çalıştırma yapılandırması

Android projeleri için yapılandırma çalıştırma belirli bir etkinlik, hizmet veya yayın alıcısının, projeyi çalıştırırken veya hata ayıklarken başlatılacak şekilde belirtilmesine izin verir. Farklı başlatma koşullarında bileşenlerinizi test etmek için amaç ek verileri geçirebilir ve amaç bayrakları ayarlayabilirsiniz.

' Den farklı etkinliklerin, `MainLauncher` `Exported=true` fiziksel bir cihazda hata ayıklama için etkinlik özniteliğine eklenmesi veya tanımlanmış amaç filtreleri olması gerekir.

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