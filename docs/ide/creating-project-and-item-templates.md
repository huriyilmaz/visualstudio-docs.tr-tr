---
title: Projeler ve dosyalar için şablonlar
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2cc932a2407aeb4951bab970a0edc6e2b2a5fcc9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301953"
---
# <a name="project-and-item-templates"></a>Proje ve madde şablonları

Proje ve madde şablonları, kullanıcılara kendi amaçları için özelleştirebilecekleri bazı temel kod ve yapı sağlayan yeniden kullanılabilir saplamalar sağlar.

## <a name="visual-studio-templates"></a>Visual Studio şablonları

Visual Studio ile önceden tanımlanmış bir dizi proje ve öğe şablonu yüklenir. **web uygulaması ve** Sınıf **Kitaplığı** şablonları ASP.NET gibi bu şablonlar, yeni bir proje oluşturduğunuzda seçim yapmak için kullanılabilir. Kod dosyaları, XML dosyaları, HTML sayfaları ve Stil Sayfaları gibi **öğe** şablonları Yeni Öğe Ekle penceresinde görünür.

Bu şablonlar, kullanıcıların proje oluşturmaya başlaması veya varolan projeleri genişletmesi için bir başlangıç noktası sağlar. Proje şablonları, belirli bir proje türü için gerekli olan dosyaları sağlar, standart derleme başvuruları içerir ve varsayılan proje özelliklerini ve derleyici seçeneklerini ayarlar. Öğe şablonları, belirli bir dosya uzantısı olan tek bir boş dosyadan saplama koduna sahip birden çok kaynak kodu dosyasına, tasarımcı bilgi dosyalarına ve katıştırılmış kaynaklara kadar karmaşıklık içinde olabilir.

Yüklü şablonları kullanabilir, kendi özel şablonlarınızı yazabilir veya topluluk tarafından oluşturulan şablonları indirebilir ve kullanabilirsiniz. Daha fazla bilgi için [bkz: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md) ve [nasıl oluşturulacak: Öğe şablonları oluşturma.](../ide/how-to-create-item-templates.md)

## <a name="contents-of-a-template"></a>Şablonun içeriği

Visual Studio ile yüklü veya sizin yeriniz tarafından oluşturulan tüm proje ve öğe şablonları, aynı ilkeleri kullanarak çalışır ve benzer içeriklere sahiptir. Tüm şablonlar aşağıdaki öğeleri içerir:

- Şablon kullanıldığında oluşturulacak dosyalar. Bu dosyalar kaynak kod dosyalarını, katıştırılmış kaynakları, proje dosyalarını ve benzeri öğeleri içerir.

::: moniker range="vs-2017"

- Şablondan bir proje veya öğe oluşturmak ve **Şablonu Yeni Proje** ve **Yeni Öğe Ekle** pencerelerinde görüntülemek için gereken meta verileri içeren *.vstemplate* dosyası.

::: moniker-end

::: moniker range=">=vs-2019"

- Şablondan bir proje veya öğe oluşturmak ve şablonu **yeni bir proje sayfası oluşturma** veya Yeni Öğe **Ekle** iletişim kutusunda görüntülemek için gereken meta verileri içeren *.vstemplate* dosyası.

::: moniker-end

   *.vstemplate* dosyaları hakkında daha fazla bilgi için [Şablon etiketleri](template-tags.md) ve [Şablon parametreleri'ne](../ide/template-parameters.md)bakın.

Bu dosyalar *bir .zip* dosyasına sıkıştırıldığında ve doğru klasöre konulduğunda, Visual Studio bunları otomatik olarak aşağıdaki yerlerde görüntüler:

::: moniker range="vs-2017"

- Proje şablonları **Yeni Proje** penceresinde görünür.

::: moniker-end

::: moniker range=">=vs-2019"

- Proje şablonları **yeni bir proje oluştur** sayfasında görünür.

::: moniker-end

- Öğe şablonları **Yeni Öğe Ekle** penceresinde görünür.

Şablon klasörleri hakkında daha fazla bilgi için [bkz.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılı: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl yapılı: Öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [Şablon etiketleri](template-tags.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio şablonlarında NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)
