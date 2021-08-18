---
title: Mimari analizi & modelleme araçları
description: Uygulamanıza mimari gereksinimlerin uygun olduğundan emin olmak için uygulama tasarlama ve modelleme.
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d191318172700a12552341c5bd3c7a2c03e63734
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157611"
---
# <a name="analyze-and-model-your-architecture"></a>Mimarinizi çözümleme ve mimarinizin modelini oluşturma

Uygulamanızı tasarlamak ve modellemek için Visual Studio mimari ve modelleme araçlarını kullanarak mimari gereksinimleri karşılar.

1. Kod yapısı, davranışı ve [kod eşlemeleri ve bağımlılık](visualize-code.md) diyagramları ile ilişkileri görselleştirerek mevcut program kodunu daha iyi anlıyoruz.
    - Kod eşlemeleri oluşturarak kodun kuruluşuna ve **ilişkilerine bakın.** 
    - Derlemeler, ad alanları, sınıflar, yöntemler gibi bağımlılıkları görselleştirin.
    - Kodu doğrulamak için bağımlılık diyagramları oluşturarak **kodunuzla tasarımı arasındaki** çakışmaları bulun.
    - Koddan sınıf diyagramları oluşturarak belirli bir proje için [sınıf yapısına ve üyelerine bakın.](../ide/class-designer/designing-and-viewing-classes-and-types.md)
    - [Metin tabanlı dosyalar oluşturmak için T4](../modeling/code-generation-and-t4-text-templates.md) şablonlarını kullanarak metin blokları ve şablonların içinde denetim mantığı kullanarak metin oluşturma. 
    
1. Mimari bağımlılıklara saygı duyma konusunda takımınızı eğitin.

1. Geliştirme sürecinizin bir parçası olarak uygulama yaşam döngüsü boyunca farklı ayrıntı düzeylerinde modeller oluşturun.

Bkz. [Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme.](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)

## <a name="code-maps"></a>Kod eşlemeleri

Kod eşlemeleri, kodundaki kuruluşu ve ilişkileri görmenizi sağlar.

Yapısını ve bağımlılıklarını daha iyi anlamak, güncelleştirmeyi ve önerilen değişikliklerin maliyetini tahmin etmek için program kodunu incelemek için haritaları kullanın.

Daha fazla bilgi edinin:
- [Mimari kod araçlarını yükleme](install-architecture-tools.md)
- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>Bağımlılık diyagramları

Bağımlılık diyagramları, bir uygulamanın yapısını açık bağımlılıklara sahip katmanlar veya bloklar kümesi olarak tanımlamanıza izin sağlar. Canlı doğrulama, kodda bağımlılıklar ile bağımlılık diyagramında açıklanan bağımlılıklar arasındaki çakışmaları gösterir.

Bağımlılık diyagramlarını kullanarak: 
- Yaşam süresi boyunca çok sayıda değişiklikle uygulamanın yapısını kararlı hale getirebilirsiniz.
- Kodda yapılan değişiklikleri denetlemeden önce, gerekmeden bağımlılık çakışmalarını keşfedin.

Daha fazla bilgi edinin:
- [Mimari kod araçlarını yükleme](install-architecture-tools.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>Etki alanına özgü dil (DSL) modelleri

DSL, belirli bir amaç için tasarlasanız bir ifadedir. Bu Visual Studio genellikle grafikseldir.

Etki alanına özgü dili kullanarak: 
- Uygulamanın bölümlerini oluşturma veya yapılandırma. Nota ve araçları geliştirmek için çalışma gerekir. Sonuç, UML özelleştirmesi yerine etki alanınıza daha uygun olabilir.
- DSL geliştirme yatırımını ve araçlarının birden fazla projede kullanımıyla geri döndürül olduğu büyük projeler veya ürün hatları için.

Daha fazla bilgi edinin:
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Mimari ve modelleme araçları için sürüm desteği

Visual Studio sürümleri mevcuttur. Bunların hepsi mimari ve modelleme araçları için destek sağlamamaktadır. Aşağıdaki tabloda her aracın kullanılabilirliği gösterir.

|**Özellik**|**Enterprise sürümü**|**Professional sürümü**|**Community sürümü**|
|-|-|-|-|
|**Kod eşlemeleri**|Yes|Yalnızca kod eşlemelerini okumayı, kod haritalarını filtrelemeyi, yeni genel düğümler eklemeyi ve seçimden yeni bir Graph oluşturmayı destekler.|-|
|**Bağımlılık diyagramları**|Yes|Yalnızca bağımlılık diyagramlarını okumayı destekler.|Yalnızca bağımlılık diyagramlarını okumayı destekler.|
|**Yönlendiren grafikler** (DGML diyagramları)|Yes|Yes|Yes|
|**Kod kopyalama**|Yes|-|-|
