---
title: Mimarinizi çözümleme ve mimarinizin modelini oluşturma
description: Uygulamanızın mimari gereksinimleri karşıladığından emin olmak için uygulamanızı tasarlamak ve modellemek üzere Visual Studio mimarisi ve modelleme araçlarını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7364da54179b742dc3cbfcd94622308f5c13b483
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861926"
---
# <a name="analyze-and-model-your-architecture"></a>Mimarinizi çözümleme ve mimarinizin modelini oluşturma

Uygulamanızı tasarlamak ve modellemek için Visual Studio mimarisi ve modelleme araçlarını kullanarak uygulamanızın mimari gereksinimleri karşıladığından emin olun.

* Kodun yapısını, davranışını ve ilişkilerini görselleştirmek için Visual Studio kullanarak mevcut program kodunu daha kolay bir şekilde anlayın.

* Mimari bağımlılıklarını önceden oluşturmanız için takımınızı eğitin.

* Geliştirme sürecinizin bir parçası olarak uygulama yaşam döngüsü boyunca farklı ayrıntı düzeylerinde modeller oluşturun.

Bkz. [Senaryo: görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Makale başvurusu

|Senaryo|Makaleler|
|-|-|
|**Kodu görselleştirin**:<br /><br />-Kod haritaları oluşturarak kodun kuruluşuna ve ilişkilerine bakın. Derlemeler, ad alanları, sınıflar, yöntemler vb. arasındaki bağımlılıkları görselleştirin.<br />-Koddan sınıf diyagramları oluşturarak belirli bir proje için sınıf yapısına ve üyelere bakın.<br />-Kodu doğrulamak için bağımlılık diyagramları oluşturarak kodunuz ve tasarımı arasında çakışmalar bulun.|- [Kodu görselleştirme](../modeling/visualize-code.md)<br />- [Sınıflarla ve diğer türlerle çalışma (Sınıf Tasarımcısı)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [Video: Visual Studio 2015 kod haritaları ile koddan tasarımı anlama](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [Video: mimari bağımlılıklarınızı gerçek zamanlı olarak doğrulama](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Mimariyi tanımlayın**:<br /><br />-Bağımlılık diyagramları oluşturarak kodunuzun bileşenleri arasındaki bağımlılıklarda kısıtlama belirleyin ve uygulayın.|- [Video: Visual Studio ile mimari bağımlılıklarını doğrulama (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Gereksinimleri ve hedeflenen tasarımı kullanarak sisteminizi doğrulayın:**<br /><br />-Hedeflenen mimariyi betimleyen ve tasarımla çakışabilecek değişiklikleri önleyen bağımlılık diyagramlarıyla kod bağımlılıklarını doğrulayın.|- [Video: Visual Studio ile mimari bağımlılıklarını doğrulama (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Modelleri ve diyagramları özelleştirme**:<br /><br />-Kendi etki alanına özgü dillerinizi oluşturun.|- [Visual Studio için modelleme SDK-Domain-Specific dilleri](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**T4 şablonlarını kullanarak metin oluştur**:<br /><br />-Metin tabanlı dosyalar oluşturmak için şablonlar içindeki metin bloklarını ve denetim mantığını kullanın.<br /> -T4 şablonu Visual Studio 'Ya dahil edilen MSBuild ile derleme|- [Kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md)|
|**Team Foundation sürüm denetimi 'ni kullanarak modelleri, diyagramları ve kod eşlemelerini paylaşma**:<br /><br />-Bunları paylaşmak için, Team Foundation sürüm denetimi altına kod haritaları, projeler ve bağımlılık diyagramları koyun.| |

Hangi Visual Studio sürümlerini her bir özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Model türleri ve tipik kullanımlar

### <a name="code-maps"></a>Kod eşlemeleri

Kod haritaları kodunuzda organizasyonu ve ilişkileri görmenizi de yardımcı olur.

**Tipik kullanımlar:**

- Yapısını ve bağımlılıklarını daha iyi anlayabilmeniz için program kodunu inceleyin, bunu nasıl güncelleştirebileceğinizi ve önerilen değişikliklerin maliyetini tahmin edebilirsiniz.

**Bakýn**

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Bağımlılık diyagramları

Bağımlılık diyagramları, bir uygulamanın yapısını açık bağımlılıklara sahip bir katman veya blok kümesi olarak tanımlamanızı sağlar. Canlı doğrulama, bir bağımlılık diyagramında açıklanan koddaki ve bağımlılıklarda bağımlılıklar arasındaki çakışmaları gösterir.

**Tipik kullanımlar:**

- Uygulamanın yapısını ömrü boyunca çok sayıda değişiklikle sabitleştir.
- Koda yapılan değişiklikleri iade etmeden önce istemeden bağımlılık çakışmalarını bulun.

**Bakýn**

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Etki alanına özgü dil (DSL)

DSL, belirli bir amaç için tasarladığınız bir gösterimidir. Visual Studio 'da genellikle grafik olur.

**Tipik kullanımlar:**

- Uygulamanın parçalarını oluşturun veya yapılandırın. Gösterimi ve araçları geliştirmek için çalışma gerekir. Sonuç, UML özelleştirmesinden daha iyi bir şekilde etki alanına uygun olabilir.
- Büyük projeler veya DSL ve araçları geliştirmedeki yatırımın birden fazla projede kullanımı tarafından döndürüldüğünden oluşan ürün hatları için.

**Bakýn**

- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2017 ' de modellemeye yönelik yenilikler](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps ve uygulama yaşam döngüsü yönetimi](/azure/devops/user-guide/devops-alm-overview)
