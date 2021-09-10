---
title: Proje ve Çözüm Özelliklerini Yönetme
description: Bu makalede, Mac için Visual Studio'de projelerin ve çözümlerin özelliklerini yönetme açık Mac için Visual Studio
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964783"
---
# <a name="managing-project-and-solution-properties"></a>Proje ve Çözüm Özelliklerini Yönetme

## <a name="project-options"></a>Proje seçenekleri

Project seçenekleri her projeye özeldir ve projenin nasıl yazıldığı, nasıl yazıldığı ve çalıştırıldığı etkiler. Kullanıcıya Mac için Visual Studio tercihlerin aksine, proje seçenekleri proje (.csproj) dosyasında depolanır, böylece diğer geliştiriciler projeyi doğru şekilde oluşturabilir ve çalıştırabilir. Belirli proje seçeneklerine sahip olmak, birçok geliştiricinin dosyanın biçimlendirmesini tehlikeye atmadan aynı belge üzerinde çalışmasına olanak sağlar.

Aşağıdaki Project açmak Mac için Visual Studio proje adına çift tıklayın veya sağ tıklar ve ardından Seçenekler'i **seçin:**

![Bağlam Menüsündeki Seçenek](media/projects-and-solutions-image2.png)

Düzenlenebilir seçenekler, kaynak kodu ve sürüm denetimi oluşturma, çalıştırma ve ayarlama seçeneklerini içerir.

Project seçenekleri beş farklı kategoriye ayrılır:

* **Genel** - Project, Açıklama ve Varsayılan Ad Alanı gibi genel bilgiler burada projenin Konumu ile birlikte ayarlanır.
* **Derleme** - Taşınabilir Sınıf Kitaplıkları için PCL profillerini ayarlamak veya değiştirmek için kullanılır. Ayrıca özel komutların, yapılandırmaların ve derleyici seçeneklerinin de ayarlandırabilirsiniz. Çıkış yolu ve derleme adı burada da ayarlandır.
* **Çalıştır** - Proje başına özel çalıştırma yapılandırmaları oluşturmak için kullanılır.
* **Kaynak Kodu** - Birçok farklı dosya türü ve adlandırma kuralının biçimlendirmesini kontrol eder. Adlandırma ilkelerini ve varsayılan üst bilgi stillerini burada da değiştirebilirsiniz.
* **Sürüm Denetimi** - Projeniz ile Sürüm Denetimi kullanırken işleme iletilerinin stilini ayarlama seçenekleri.

Platforma bağlı olarak her proje belirli proje seçeneklerini içerebilir. Örneğin, aşağıdaki görüntüde gösterildiği gibi bir Xamarin.Android projesinin, Android derlemesi (örneğin, bağlantıcı seçenekleri) ve Uygulama (izinler gibi) ile ilgili seçenekleri vardır:

![Android Project Seçenekleri](media/projects-and-solutions-image5.png)

Xamarin.iOS'un paket imzalamayla ilgili seçenekleri vardır; örneğin, kullanmak için gerekli sağlama profili:

![iOS Project Seçenekleri](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Çözüm Seçenekleri

Çözüm seçenekleri, Project seçeneklerine benzer, ancak çözümlerin tamamının kapsamını içerir. Yazar bilgilerini, derleme ayarlarını, kod biçimlendirme stillerini ve sürüm denetimi ayarlamanın bir yolunu sağlar ve Çözüm'de başlangıç projesi atamanın bir yolunu sağlar.  Çözüm Seçenekleri iletişim kutusuna **Project >** Seçenekleri menü öğesinden, Çözüm  Penceresindeki Çözüm'de Seçenekler bağlam menüsü öğesinden veya Çözüm Penceresinde Çözüm'e çift tıklayarak erişilebilir:

![Çözüm Seçenekleri](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Ayrıca bkz.

* [Proje ve çözüm özelliklerini yönetme (Visual Studio Windows)](/visualstudio/ide/managing-project-and-solution-properties)