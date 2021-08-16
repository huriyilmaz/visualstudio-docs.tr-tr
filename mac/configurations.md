---
title: Yapı Yapılandırmalarını Anlama
description: Bu makalede, Mac için Visual Studio'daki çeşitli derleme yapılandırmaları açık Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 9b04c709f5bfe40e1906aaebb501ac427631119165486c3ac4d63d0ff7cdae7f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121364930"
---
# <a name="understanding-build-configurations"></a>Yapı yapılandırmalarını anlama

Geliştirme işlemi sırasında farklı türlerde derlemelerde kullanmak üzere çözüm ve proje özelliklerinin farklı yapılandırmalarını depolayın. Şablon kullanılarak Mac için Visual Studio projeler genellikle bir uygulamanın hata ayıklamasını ve bir uygulamanın dağıtımını destekleyen Hata Ayıklama ve Sürüm yapılandırmalarını içerir. 

Özel yapılandırmalar oluşturmak için bkz. Derleme [yapılandırmalarını oluşturma ve düzenleme.](./create-and-edit-configurations.md)

>[!NOTE]
>Bu konu, Mac için Visual Studio. Daha Visual Studio için Windows [yapılandırmalarını anlama.](/visualstudio/ide/understanding-build-configurations)

## <a name="solution-configurations"></a>Çözüm yapılandırmaları

Çözüm yapılandırmaları, bir çözümde yer alan tüm projelerin yapılandırmalarını belirtmek için kullanılır. Derleme **Yapılandırmaları öğesi altındaki** Yapılandırma Eşlemeleri **>** kullanarak, açılan çözümde her öğe için bir hedef yapılandırma atabilirsiniz. Bu, aşağıdaki görüntüde gösterildi:

![Yapılandırma Eşleme Seçenekleri](media/projects-and-solutions-image3.png)

Yapılandırmalar hakkında daha fazla bilgi için James Montemagno [Yapılandırma Yöneticisi](https://www.youtube.com/watch?v=tjSdkqYh5Vg) videosunu izleyin.

## <a name="project-build-configurations"></a>Project yapılandırmaları oluşturma

Projelerin birden çok yapılandırması vardır. Proje hedeflerini yapılandırma ve platform birlikte kullanarak, proje yapılandırmasını yapılandırmasını yapmak için kullanılacak özellikleri belirtir. Yapılandırmalar arasında geçiş yapmak, derleme zamanında farklı çıkışlara olanak sağlar. Örneğin, hata ayıklama yapılandırması hata ayıklama sembolleri çıkışı vererek hata ayıklayıcının, kilitlenmeye neden olan bir uygulamanın yığın izlemesi işlev adlarını, parametrelerini veya değişkenlerini çözümlemesini sağlar. Bu ek bilgiler geliştirme sırasında yararlı olur ancak şişirilmiş bir dosya boyutuna yol açsa da dağıtım için ideal değildir.

Her platformun derlemesi için belirli yapılandırmalar vardır. Projelerin derleme yapılandırma sayfalarına, Proje Seçenekleri iletişim kutusundaki **Derleme** bölümüne **Project erişilebilir.** Projeye sağ tıklar ve Seçenekler'i  seçerek veya çözüm gezgininde projeye çift tıklayarak bu iletişim kutusunu açın.

## <a name="run-configuration"></a>Yapılandırmayı çalıştırma

Mac için Visual Studio bir çalıştırma yapılandırması _ayarlamaya olanak sağlar._ Çalıştırma yapılandırmaları aşağıda gösterildiği gibi, araç çubuğunda, derleme yapılandırma seçicinin yanında bir açılan listede görüntülenir:

![Yapılandırmayı Çalıştır açılan listesinde](media/projects-and-solutions-image8.png)

Çalıştırma yapılandırması, bir ad ve farklı amaçlar için projede tanımlanan çeşitli yapılandırmalara sahip bir yürütme seçenekleri kümesidir. Çalıştırma yapılandırmaları proje düzeyinde tanımlanır ve her yürütülebilir proje için otomatik olarak bir varsayılan oluşturulur, ancak gereken sayıda ekleme mümkündür. Belirli proje türleri otomatik olarak ek çalıştırma yapılandırmaları üretir. Örneğin, watchOS projeleri Glance ve  _Notification yapılandırmaları oluşturabiliyor._

Yapılandırmalar diğer geliştiricilerle paylaşılabilir (bu durumda yapılandırmalar .csproj dosyasında depolanır) veya yerel olarak tutulabilir (bu durumda bir .user dosyasında depolanır).

### <a name="android-run-configurations"></a>Android çalıştırma yapılandırmaları

Android projeleri için çalıştırma yapılandırmaları, belirli bir etkinliğin, hizmetin veya yayın alıcısının belirtimlerinin projeyi çalıştırma veya hata ayıklama sırasında başlatılmasına olanak sağlar. Amaç ek verileri iletir ve bileşenlerinizi farklı başlatma koşulları altında test etmek için amaç bayrakları ayarlayın.

dışında etkinliklerin fiziksel bir cihazda hata ayıklama için Etkinlik özniteliğine eklenmiş veya Amaç filtreleri `MainLauncher` `Exported=true` tanımlanmıştır.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Çalıştırma yapılandırmalarında yer alan veri örnekleri

Aşağıdaki listede, çalıştırma yapılandırmalarında yer alan bazı veri örnekleri verilmiştir:

* Normal .NET projesi
  * Alternatif başlangıç uygulaması
  * Bağımsız değişkenleri başlatma
  * Çalışma dizini
  * Ortam değişkenleri
  * Mono çalışma zamanı seçenekleri (yalnızca Mono üzerinde çalıştır kullanılır)
* Android projesi
  * Giriş noktası (etkinlik, hizmet, alıcı)
  * Amaç bağımsız değişkenleri ve verileri
* iOS projesi
  * Mod (Normal, Arka Plan Getirme)
* iOS uzantısı projesi
  * Başlangıç uygulaması: varsayılan veya özel
* WatchKit projesi
  * Mod (Glance, Notification)
  * Bildirim yükü

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmalarını anlama (Visual Studio Windows)](/visualstudio/ide/understanding-build-configurations)