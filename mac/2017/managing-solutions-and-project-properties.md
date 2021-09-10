---
title: Proje ve Çözüm Özelliklerini Yönetme
description: bu makalelerde Mac için Visual Studio içindeki projelerin ve çözümlerin özelliklerinin nasıl yönetileceği açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962242"
---
# <a name="managing-project-and-solution-properties"></a>Proje ve Çözüm Özelliklerini Yönetme

## <a name="project-options"></a>Proje seçenekleri

Project seçenekler her bir projeye özgüdür ve projenin nasıl yazıldığını, oluşturulduğunu ve çalıştırılacağını etkiler. bu, Mac için Visual Studio tercihleri (kullanıcıya özgü seçenekleri ayarlayan) ve çözüm seçeneklerini (çözümün tamamına yönelik seçenekleri belirler) ile karşıttır. Project seçenekler proje (. csproj) dosyasında depolanır, böylece diğer geliştiricilerin projeyi doğru bir şekilde oluşturup çalıştırabilmesini sağlayın. Belirli proje seçeneklerinin olması, birçok geliştiricinin dosya biçimlendirmesini tehlikeye atmadan aynı belgede çalışmasına izin verir.

Mac için Visual Studio Project seçeneklerini açmak için, proje adına çift tıklayın veya bağlam menüsünü açmak için sağ tıklayın ve ardından **seçenekler**' i seçin:

![Bağlam menüsündeki seçeneği](media/projects-and-solutions-image2.png)

Düzenlenebilir seçenekler, kaynak kodu ve sürüm denetimi oluşturma, çalıştırma ve ayarlama seçeneklerini içerir.

Project seçenekler beş farklı kategoride düzenlenmiştir:

* ad, açıklama ve varsayılan ad alanı gibi **genel** -Project bilgiler, projenin konumuyla birlikte burada ayarlanır.
* **Build** -bu, geliştiricilerin taşınabilir sınıf KITAPLıKLARı için PCL profillerini ayarlamasına veya değiştirmesine olanak tanır. Ayrıca özel komutların, yapılandırmaların, derleyici seçeneklerinin ayarlanmalarına izin verir. Çıktı yolu ve derleme adı da burada ayarlanabilir.
* **Çalıştır** -bu, proje temelinde özel çalışma yapılandırmalarının oluşturulmasına olanak sağlar.
* **Kaynak kodu** -bu, birçok farklı dosya türü ve adlandırma kuralı biçimlendirmesini denetlemenize olanak tanır. Ayrıca, adlandırma ilkelerini ve varsayılan üstbilgi stillerini burada da ayarlayabilirsiniz.
* **Sürüm denetimi** -bu, projeniz Ile sürüm denetimini kullanırken, COMMIT iletisinin stilini düzenlemenizi sağlar.

Her proje platforma bağlı olarak belirli proje seçeneklerini içerebilir. Örneğin, aşağıdaki görüntüde gösterildiği gibi bir Xamarin. Android projesi, Android derlemesi (bağlayıcı seçenekleri gibi) ve uygulama (izinler gibi) ile ilgili seçeneklere sahiptir:

![Android Project seçenekleri](media/projects-and-solutions-image5.png)

Xamarin. iOS, kullanılacak gerekli sağlama profili gibi paket imzalama ile ilgili seçeneklere sahiptir:

![iOS Project seçenekleri](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Çözüm seçenekleri

çözüm seçenekleri Project seçenekler gibidir, ancak tüm çözümlerin kapsamını kapsar. Yazar bilgilerini, derleme ayarlarını, kod biçimlendirme stillerini ve sürüm denetimini ayarlamak için bir yol sağlar ve çözüm içinde başlangıç projesini atamak için bir yol sağlar.  çözüm seçenekleri iletişim kutusuna **Project > çözüm seçenekleri** menü öğesinden, çözüm panelinde çözümdeki **seçenekler** bağlam menü öğesinden veya Çözüm Bölmesi çözüme çift tıklanarak erişilebilir:

![Çözüm seçenekleri](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

* [proje ve çözüm özelliklerini yönetme (Windows Visual Studio)](/visualstudio/ide/managing-project-and-solution-properties)