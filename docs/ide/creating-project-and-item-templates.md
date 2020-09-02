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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89313802"
---
# <a name="project-and-item-templates"></a>Proje ve öğe şablonları

Proje ve öğe şablonları, kullanıcılara kendi amaçlarına göre özelleştirebilecekleri bazı temel kod ve yapıları sağlayan yeniden kullanılabilir saplamalar sağlar.

## <a name="visual-studio-templates"></a>Visual Studio şablonları

Bir dizi önceden tanımlanmış proje ve öğe şablonu, Visual Studio ile birlikte yüklenir. **ASP.NET Web uygulaması** ve **sınıf kitaplığı** şablonları gibi bu şablonlar, yeni bir proje oluşturduğunuzda arasından seçim yapmak için kullanılabilir. Kod dosyaları, XML dosyaları, HTML sayfaları ve stil sayfaları gibi öğe şablonları, **Yeni öğe Ekle** penceresinde görünür.

Bu şablonlar, kullanıcıların proje oluşturmaya başlaması için bir başlangıç noktası sağlar veya mevcut projeleri genişletir. Proje şablonları, belirli bir proje türü için gereken dosyaları sağlar, standart derleme başvurularını dahil eder ve varsayılan proje özelliklerini ve derleyici seçeneklerini ayarlar. Öğe şablonları, belirli bir dosya uzantısına sahip tek bir boş dosyanın karmaşıklık halinde, saplama kodu, tasarımcı bilgi dosyaları ve katıştırılmış kaynaklarla birden çok kaynak kodu dosyasına sahip olabilir.

Yüklü şablonları kullanabilir, kendi özel şablonlarınızı yazabilir veya topluluk tarafından oluşturulan şablonları indirebilir ve kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md) ve [nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Şablonun içeriği

Tüm proje ve öğe şablonları, Visual Studio ile yüklenip, sizin tarafınızdan oluşturulmuş olsun, aynı ilkeleri kullanarak çalışır ve benzer içeriğe sahiptir. Tüm şablonlar aşağıdaki öğeleri içerir:

- Şablon kullanıldığında oluşturulacak dosyalar. Bu dosyalar kaynak kodu dosyalarını, katıştırılmış kaynakları, proje dosyalarını vb. içerir.

::: moniker range="vs-2017"

- Şablondan bir proje veya öğe oluşturmak ve şablonu **Yeni projede** göstermek ve **Yeni öğe pencereleri eklemek** için gereken meta verileri içeren bir *. vstemplate* dosyası.

::: moniker-end

::: moniker range=">=vs-2019"

- Şablondan bir proje veya öğe oluşturmak ve şablonu **Yeni proje oluştur** sayfasında veya **Yeni öğe Ekle** iletişim kutusunda göstermek için gereken meta verileri içeren bir *. vstemplate* dosyası.

::: moniker-end

   *. Vstemplate* dosyaları hakkında daha fazla bilgi için bkz. [Şablon Etiketleri](template-tags.md) ve [şablon parametreleri](../ide/template-parameters.md).

Bu dosyalar bir *. zip* dosyasında sıkıştırıldığında ve doğru klasöre koyduğunuzda, Visual Studio bunları otomatik olarak aşağıdaki yerlerde görüntüler:

::: moniker range="vs-2017"

- Proje şablonları **Yeni proje** penceresinde görünür.

::: moniker-end

::: moniker range=">=vs-2019"

- Proje şablonları **Yeni proje oluştur** sayfasında görünür.

::: moniker-end

- Öğe şablonları **Yeni öğe Ekle** penceresinde görünür.

Şablon klasörleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [Şablon etiketleri](template-tags.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio şablonlarındaki NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)
