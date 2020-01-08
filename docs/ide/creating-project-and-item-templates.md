---
title: Projeleri ve dosyaları için şablonlar
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589766"
---
# <a name="project-and-item-templates"></a>Proje ve öğe şablonları

Proje ve öğe şablonları, bazı temel kod ve kendi amaçları için özelleştirebilecekleri yapısı, kullanıcılara vermek yeniden kullanılabilir saptamalar sağlar.

## <a name="visual-studio-templates"></a>Visual Studio şablonları

Bir dizi önceden tanımlanmış proje ve öğe şablonları, Visual Studio ile yüklenir. **ASP.NET Web uygulaması** ve **sınıf kitaplığı** şablonları gibi bu şablonlar, yeni bir proje oluşturduğunuzda arasından seçim yapmak için kullanılabilir. Kod dosyaları, XML dosyaları, HTML sayfaları ve stil sayfaları gibi öğe şablonları, **Yeni öğe Ekle** penceresinde görünür.

Bu şablonlar, proje oluşturmaya başlamak için veya mevcut projeleri genişletmek için kullanıcılar için bir başlangıç noktası sağlar. Proje şablonları, belirli proje türü için gerekli dosyaları sağlar, standart derleme başvurularını içerir ve varsayılan proje özellikleri ve derleyici seçeneklerini ayarlayın. Öğe şablonları, birden çok kaynak kodu dosyaları saplama kodla, Tasarımcı bilgi dosyaları ve gömülü kaynaklar belirli dosya uzantısına sahip tek bir boş dosya karmaşıklığı değişebilir.

Yüklü şablonları kullanabilir, kendi özel şablonlarınızı yazabilir veya topluluk tarafından oluşturulan şablonları indirebilir ve kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md) ve [nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Bir şablon içeriği

Tüm proje ve öğe şablonları, Visual Studio ile yüklenir veya sizin tarafınızdan oluşturulan aynı ilkeleri kullanarak işlev ve benzer içeriğe sahip. Tüm şablonları aşağıdaki öğeleri içerir:

- Şablonu kullanıldığında oluşturulan dosyalar. Bu dosyalar, kaynak kodu dosyaları, katıştırılmış kaynaklar, proje dosyaları vb. içerir.

::: moniker range="vs-2017"

- Şablondan bir proje veya öğe oluşturmak ve şablonu **Yeni projede** göstermek ve **Yeni öğe pencereleri eklemek** için gereken meta verileri içeren bir *. vstemplate* dosyası.

::: moniker-end

::: moniker range=">=vs-2019"

- Şablondan bir proje veya öğe oluşturmak ve şablonu **Yeni proje oluştur** sayfasında veya **Yeni öğe Ekle** iletişim kutusunda göstermek için gereken meta verileri içeren bir *. vstemplate* dosyası.

::: moniker-end

   *. Vstemplate* dosyaları hakkında daha fazla bilgi için bkz. [Şablon Etiketleri](template-tags.md) ve [şablon parametreleri](../ide/template-parameters.md).

Ne zaman bu dosyaları sıkıştırılır içine bir *.zip* dosya ve doğru klasöre yerleştirin, Visual Studio otomatik olarak aşağıdaki konumlarda görüntüler:

::: moniker range="vs-2017"

- Proje şablonları **Yeni proje** penceresinde görünür.

::: moniker-end

::: moniker range=">=vs-2019"

- Proje şablonları **Yeni proje oluştur** sayfasında görünür.

::: moniker-end

- Öğe şablonları **Yeni öğe Ekle** penceresinde görünür.

Şablon klasörleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
- [Şablon Etiketleri](template-tags.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio şablonları NuGet paketleri](/nuget/visual-studio-extensibility/visual-studio-templates)
