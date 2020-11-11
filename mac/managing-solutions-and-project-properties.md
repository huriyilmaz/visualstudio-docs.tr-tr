---
title: Proje ve Çözüm Özelliklerini Yönetme
description: Bu makalede Mac için Visual Studio içindeki projelerin ve çözümlerin özelliklerinin nasıl yönetileceği açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493003"
---
# <a name="managing-project-and-solution-properties"></a>Proje ve Çözüm Özelliklerini Yönetme

## <a name="project-options"></a>Proje seçenekleri

Proje seçenekleri her bir projeye özeldir ve projenin nasıl yazıldığını, oluşturulduğunu ve çalıştırılacağını etkiler. Kullanıcıya özgü ayarlar olan Mac için Visual Studio tercihlerinden farklı olarak, diğer geliştiricilerin projeyi doğru bir şekilde oluşturup çalıştırabilmeleri için proje seçenekleri proje (. csproj) dosyasında depolanır. Belirli proje seçeneklerinin olması, birçok geliştiricinin dosya biçimlendirmesini tehlikeye atmadan aynı belgede çalışmasına izin verir.

Proje seçeneklerini Mac için Visual Studio açmak için, proje adına çift tıklayın veya bağlam menüsünü açmak için sağ tıklayın ve ardından **Seçenekler** ' i seçin:

![Bağlam menüsündeki seçeneği](media/projects-and-solutions-image2.png)

Düzenlenebilir seçenekler, kaynak kodu ve sürüm denetimi oluşturma, çalıştırma ve ayarlama seçeneklerini içerir.

Proje seçenekleri beş farklı kategoride düzenlenmiştir:

* **Genel** -ad, açıklama ve varsayılan ad alanı gibi proje bilgileri, projenin konumuyla birlikte burada ayarlanır.
* **Oluşturma** -taşınabilir sınıf kitaplıklarının PCL profillerini ayarlamak veya değiştirmek için kullanılır. Ayrıca özel komutların, yapılandırmaların, derleyici seçeneklerinin ayarlanmalarına izin verir. Çıktı yolu ve derleme adı da burada ayarlanabilir.
* **Çalıştır** -proje temelinde özel çalışma yapılandırması oluşturmak için kullanılır.
* **Kaynak kodu** -birçok farklı dosya türü ve adlandırma kuralı biçimlendirmesini denetler. Ayrıca, adlandırma ilkelerini ve varsayılan üstbilgi stillerini burada da ayarlayabilirsiniz.
* **Sürüm denetimi** -projeniz Ile sürüm denetimini kullanırken, tamamlama iletilerinin stilini ayarlamaya yönelik seçenekler.

Her proje platforma bağlı olarak belirli proje seçeneklerini içerebilir. Örneğin, aşağıdaki görüntüde gösterildiği gibi bir Xamarin. Android projesi, Android derlemesi (bağlayıcı seçenekleri gibi) ve uygulama (izinler gibi) ile ilgili seçeneklere sahiptir:

![Android proje seçenekleri](media/projects-and-solutions-image5.png)

Xamarin. iOS, kullanılacak gerekli sağlama profili gibi paket imzalama ile ilgili seçeneklere sahiptir:

![iOS proje seçenekleri](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Çözüm seçenekleri

Çözüm seçenekleri proje seçenekleri gibidir, ancak tüm çözümlerin kapsamını kapsar. Yazar bilgilerini, derleme ayarlarını, kod biçimlendirme stillerini ve sürüm denetimini ayarlamak için bir yol sağlar ve çözüm içinde başlangıç projesini atamak için bir yol sağlar.  Çözüm seçenekleri iletişim kutusuna **proje > çözüm seçenekleri** menü öğesinden, çözüm penceresindeki çözümdeki **Seçenekler** bağlam menü öğesinden veya çözüm penceresindeki çözüme çift tıklayarak erişilebilir:

![Çözüm seçenekleri](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

* [Proje ve çözüm özelliklerini yönetme (Windows üzerinde Visual Studio)](/visualstudio/ide/managing-project-and-solution-properties)