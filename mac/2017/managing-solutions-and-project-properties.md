---
title: Proje ve Çözüm Özelliklerini Yönetme
description: Bu makale, Mac için Visual Studio'daki projelerin ve çözümlerin özelliklerini nasıl yöneteceklerini açıklar
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985259"
---
# <a name="managing-project-and-solution-properties"></a>Proje ve Çözüm Özelliklerini Yönetme

## <a name="project-options"></a>Proje seçenekleri

Proje seçenekleri her projeye özgüdür ve projenin nasıl yazıldığı, inşa edilip çalıştırıldığını etkiler. Bu, Mac Tercihleri için Visual Studio (kullanıcıya özel seçenekleri ayarlar) ve Çözüm seçenekleriyle (tüm çözüm için seçenekler ayarlayan) ile tezat ayarı. Proje seçenekleri proje (.csproj) dosyasında depolanır, böylece diğer geliştiriciler projeyi doğru bir şekilde oluşturabilir ve çalıştırabilir. Belirli proje seçeneklerine sahip olmak, birçok geliştiricinin dosyanın biçimlendirmesini tehlikeye atmadan aynı belge üzerinde çalışmasına olanak tanır.

Mac için Visual Studio'da Proje seçeneklerini açmak için proje adını çift tıklatın veya bağlam menüsünü açmak için sağ tıklatın ve **ardından Seçenekler'i**seçin:

![Bağlam Menüsünde Seçenek](media/projects-and-solutions-image2.png)

Kullanılabilir seçenekler, kaynak kodu ve sürüm denetimi oluşturma, çalıştırma ve ayarlama seçeneklerini içerir.

Proje seçenekleri beş farklı kategoride düzenlenir:

* **Genel** - Ad, Açıklama ve Varsayılan Ad Alanı gibi proje bilgileri, projenin Konumu ile birlikte burada ayarlanır.
* **Yapı** - Bu, geliştiricilerin Taşınabilir Sınıf Kitaplıkları için PCL profillerini ayarlamasına veya değiştirmesine olanak tanır. Ayrıca özel komutlar, yapılandırmalar, derleyici seçenekleri ayarlanacak sağlar. Çıktı yolu ve montaj adı da burada ayarlanabilir.
* **Çalıştır** - Bu, proje başına özel çalıştırma yapılandırmaları oluşturmanıza olanak tanır.
* **Kaynak Kodu** - Bu, birçok farklı dosya türlerinin biçimlendirmesini ve adlandırma kurallarını denetlemenize olanak tanır. Ayrıca adlandırma ilkeleri ve varsayılan üstbilgi stilleri burada ayarlayabilirsiniz.
* **Sürüm Denetimi** - Bu, projenizle Sürüm Denetimi'ni kullanırken iletinin stilini düzenlemeye olanak tanır.

Her proje, platforma bağlı olarak belirli proje seçenekleri içerebilir. Örneğin, aşağıdaki resimde gösterildiği gibi bir Xamarin.Android projesinde Android yapısı (bağlayıcı seçenekleri gibi) ve Uygulama (izinler gibi) ile ilgili seçenekler vardır:

![Android Proje Seçenekleri](media/projects-and-solutions-image5.png)

Xamarin.iOS'un paket imzalamayla ilgili seçenekleri vardır - örneğin kullanılacak gerekli sağlama profili gibi:

![iOS Proje Seçenekleri](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Çözüm Seçenekleri

Çözüm seçenekleri Proje seçenekleri gibidir, ancak tüm Çözümlerin kapsamını kapsar. Yazar bilgilerini ayarlamak, ayarlar oluşturmak, kod biçimlendirme stilleri ve sürüm denetimi sağlamak ve Çözüm'de başlangıç projesini atamanın bir yolunu sağlarlar.  Çözüm Seçenekleri iletişim kutusuna Project **> Çözüm Seçenekleri** menü öğesinden, Çözüm defterindeki **Seçenekler** bağlam ı menü öğesinden veya Çözüm Defteri'ndeki Çözüm'e çift tıklayarak erişilebilir:

![Çözüm Seçenekleri](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

* [Proje ve çözüm özelliklerini yönetme (Windows'ta Visual Studio)](/visualstudio/ide/managing-project-and-solution-properties)