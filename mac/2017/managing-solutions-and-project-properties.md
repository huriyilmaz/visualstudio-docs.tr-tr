---
title: Proje ve Çözüm Özelliklerini Yönetme
description: Bu makalelerde Mac için Visual Studio içindeki projelerin ve çözümlerin özelliklerinin nasıl yönetileceği açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985259"
---
# <a name="managing-project-and-solution-properties"></a>Proje ve Çözüm Özelliklerini Yönetme

## <a name="project-options"></a>Proje seçenekleri

Proje seçenekleri her bir projeye özeldir ve projenin nasıl yazıldığını, oluşturulduğunu ve çalıştırılacağını etkiler. Bu, Mac için Visual Studio tercihleri (kullanıcıya özgü seçenekleri ayarlayan) ve çözüm seçeneklerini (çözümün tamamına yönelik seçenekleri belirler) ile karşıttır. Proje seçenekleri, diğer geliştiricilerin projeyi doğru bir şekilde oluşturup çalıştırabilmeleri için proje (. csproj) dosyasında depolanır. Belirli proje seçeneklerinin olması, birçok geliştiricinin dosya biçimlendirmesini tehlikeye atmadan aynı belgede çalışmasına izin verir.

Proje seçeneklerini Mac için Visual Studio açmak için, proje adına çift tıklayın veya bağlam menüsünü açmak için sağ tıklayın ve ardından **Seçenekler**' i seçin:

![Bağlam menüsündeki seçeneği](media/projects-and-solutions-image2.png)

Düzenlenebilir seçenekler, kaynak kodu ve sürüm denetimi oluşturma, çalıştırma ve ayarlama seçeneklerini içerir.

Proje seçenekleri beş farklı kategoride düzenlenmiştir:

* **Genel** -ad, açıklama ve varsayılan ad alanı gibi proje bilgileri, projenin konumuyla birlikte burada ayarlanır.
* **Build** -bu, geliştiricilerin taşınabilir sınıf KITAPLıKLARı için PCL profillerini ayarlamasına veya değiştirmesine olanak tanır. Ayrıca özel komutların, yapılandırmaların, derleyici seçeneklerinin ayarlanmalarına izin verir. Çıktı yolu ve derleme adı da burada ayarlanabilir.
* **Çalıştır** -bu, proje temelinde özel çalışma yapılandırmalarının oluşturulmasına olanak sağlar.
* **Kaynak kodu** -bu, birçok farklı dosya türü ve adlandırma kuralı biçimlendirmesini denetlemenize olanak tanır. Ayrıca, adlandırma ilkelerini ve varsayılan üstbilgi stillerini burada da ayarlayabilirsiniz.
* **Sürüm denetimi** -bu, projeniz Ile sürüm denetimini kullanırken, COMMIT iletisinin stilini düzenlemenizi sağlar.

Her proje platforma bağlı olarak belirli proje seçeneklerini içerebilir. Örneğin, aşağıdaki görüntüde gösterildiği gibi bir Xamarin. Android projesi, Android derlemesi (bağlayıcı seçenekleri gibi) ve uygulama (izinler gibi) ile ilgili seçeneklere sahiptir:

![Android proje seçenekleri](media/projects-and-solutions-image5.png)

Xamarin. iOS, kullanılacak gerekli sağlama profili gibi paket imzalama ile ilgili seçeneklere sahiptir:

![iOS proje seçenekleri](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Çözüm seçenekleri

Çözüm seçenekleri proje seçenekleri gibidir, ancak tüm çözümlerin kapsamını kapsar. Yazar bilgilerini, derleme ayarlarını, kod biçimlendirme stillerini ve sürüm denetimini ayarlamak için bir yol sağlar ve çözüm içinde başlangıç projesini atamak için bir yol sağlar.  Çözüm seçenekleri iletişim kutusuna **proje > çözüm seçenekleri** menü öğesinden, çözüm panelinde çözümdeki **Seçenekler** bağlam menü öğesinden veya çözüm bölmesi çözüme çift tıklanarak erişilebilir:

![Çözüm seçenekleri](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

* [Proje ve çözüm özelliklerini yönetme (Windows üzerinde Visual Studio)](/visualstudio/ide/managing-project-and-solution-properties)