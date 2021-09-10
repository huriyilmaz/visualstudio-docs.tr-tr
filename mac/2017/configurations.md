---
title: Yapı Yapılandırmalarını Anlama
description: Bu makalede, Mac için Visual Studio'daki çeşitli derleme yapılandırmaları açık Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962122"
---
# <a name="understanding-build-configurations"></a>Yapı yapılandırmalarını anlama

## <a name="project-build-configurations"></a>Project yapılandırmaları oluşturma

Projeler birden çok yapılandırmaya sahiptir ve bu yapılandırmalar arasında geçiş yapmak derleme zamanında farklı çıkışlara olanak sağlar. Örneğin, hata ayıklama yapılandırması hata ayıklama sembolleri çıkışı vererek hata ayıklayıcının, kilitlenmeye neden olan bir uygulamanın yığın izlemesi işlev adlarını, parametrelerini veya değişkenlerini çözümlemesini sağlar. Bu ek bilgiler geliştirme sırasında yararlı olur ancak şişirilmiş bir dosya boyutuna yol açsa da dağıtım için ideal değildir.

Her platformun derlemesi için belirli yapılandırmalar vardır.

## <a name="solution-configurations"></a>Çözüm yapılandırmaları

Proje yapılandırmaları gibi çözüm yapılandırmaları da projenin tamamına özel yapılandırmalar oluşturmak için kullanılır. Derleme **Yapılandırmaları öğesi** altındaki **Yapılandırma Eşlemeleri sekmesini >,** aşağıdaki görüntüde gösterildiği gibi her çözüm öğesi için bir hedef yapılandırma atabilirsiniz:

![Yapılandırma Eşleme Seçenekleri](media/projects-and-solutions-image3.png)

Yapılandırmalar hakkında daha fazla bilgi için James Montemagno [Yapılandırma Yöneticisi](https://www.youtube.com/watch?v=tjSdkqYh5Vg) videosunu izleyin.

## <a name="run-configuration"></a>Yapılandırmayı çalıştırma

Önceki Xamarin Studio sürümlerinde, genel run/debug komutu kullanılarak çalıştır/hata ayıklandırilen proje olan bir projeyi Başlangıç Project olarak ayarlama seçeneğini kullanabilirsiniz.  Bu, proje panelinin içinde projenin adı için kalın bir yazı tipiyle belirtilmiştir.

Bu Mac için Visual Studio, başlangıç projesi ayarlamak yerine bir çalıştırma yapılandırması _ayarlayın._ Çalıştırma yapılandırmaları aşağıda gösterildiği gibi, araç çubuğundaki bir açılan listede derleme yapılandırma seçicinin yanında yer almaktadır:

![Yapılandırmayı Çalıştır açılan listesinde](media/projects-and-solutions-image8.png)

Çalıştırma yapılandırması, bir ad ve farklı amaçlar için projede tanımlanan çeşitli yapılandırmalara sahip bir yürütme seçenekleri kümesidir. Çalıştırma yapılandırmaları proje düzeyinde tanımlanır ve her yürütülebilir proje için varsayılan olarak oluşturulur, ancak gereken sayıda ekleme mümkündür. Belirli proje türleri otomatik olarak ek çalıştırma yapılandırmaları üretir. Örneğin, watchOS projeleri Glance ve  _Notification yapılandırmaları oluşturabiliyor._

Yapılandırmalar diğer geliştiricilerle paylaşılabilir (bu durumda yapılandırmalar .csproj dosyasında depolanır) veya yerel olarak tutulabilir (bu durumda bir .user dosyasında depolanır).

### <a name="android-run-configurations"></a>Android çalıştırma yapılandırmaları

Android projeleri için çalıştırma yapılandırmaları, projeyi çalıştırma veya hata ayıklama sırasında hangi etkinliğin, hizmetin veya yayın alıcısının başlatılacalarını belirtmenize olanak sağlar. Bileşenlerinizi farklı başlatma koşulları altında test etmek için amaç ek verileri iletir ve amaç bayrakları ayarlayın.

dışında etkinliklerin fiziksel bir cihazda hata ayıklama için Etkinlik özniteliğine eklenmiş veya Amaç filtreleri `MainLauncher` `Exported=true` tanımlanmıştır.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Çalıştırma yapılandırmalarında yer alan veri örnekleri

Aşağıdaki listede, çalıştırma yapılandırmalarında yer alan bazı veri örnekleri verilmiştir:

* Normal .NET projesi
  * Alternatif başlangıç uygulaması
  * Bağımsız değişkenleri başlatma
  * Çalışma dizini
  * Ortam değişkenleri
  * Mono çalışma zamanı seçenekleri (yalnızca Mono'da çalıştır kullanılırken kullanılacak)
* Android projesi
  * Giriş noktası (etkinlik, hizmet, alıcı)
  * Amaç bağımsız değişkenleri ve verileri
* iOS projesi
  * Mod (Normal, Arka Plan Getirme)
* iOS uzantı projesi
  * Başlangıç uygulaması: varsayılan veya özel
* WatchKit projesi
  * Mod (Glance, Notification)
  * Bildirim yükü

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmalarını anlama (Visual Studio Windows)](/visualstudio/ide/understanding-build-configurations)
