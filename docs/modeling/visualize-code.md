---
title: Kodu görselleştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9886ea905a4997d5735e4dd2cabbfc4798a5c4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535882"
---
# <a name="visualize-code"></a>Kodu görselleştirme

Visual Studio 'da görselleştirme ve modelleme araçlarını kullanarak mevcut kodu anlamanıza ve uygulamanızı açıklamanıza yardımcı olabilirsiniz. Bu, değişikliklerinizin kodu nasıl etkileyebileceğini görsel olarak öğrenmenize ve bu değişikliklerden kaynaklanan iş ve riskleri değerlendirmenize yardımcı olur. Örneğin:

- Kodunuzdaki ilişkileri anlamak için, bu ilişkileri görsel olarak eşleyin.

- Sisteminizin mimarisini betimleyip kodu tasarımla tutarlı tutun, bağımlılık diyagramları oluşturun ve kodu bu diyagramlarda doğrulayın.

- Sınıf yapılarını anlatmak için sınıf diyagramları oluşturun.

Bu araçlar, projenize dahil olan insanlarla daha kolay iletişim kurmanıza de yardımcı olur.

Hangi Visual Studio sürümlerini her bir özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|Senaryo|Makaleler|
|-|-|
|**Kodu ve ilişkilerini anlayın:**<br /><br /> Belirli kod parçaları arasındaki ilişkileri eşleyin.<br /><br /> Tüm çözüm için kodunuzdaki ilişkilere genel bakış bölümüne bakın.|- [Çözümleriniz genelinde bağımlılıkları eşleyin](../modeling/map-dependencies-across-your-solutions.md)<br />- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanın](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Kod Haritası Çözümleyicileri kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Sınıf yapılarını anlayın:**<br /><br /> Koddan sınıf diyagramları oluşturarak bir projedeki sınıfların yapısını görselleştirin.|[Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Üst düzey sistem tasarımını açıkla ve kodu bu tasarıma göre doğrula:**<br /><br /> Bağımlılık diyagramları oluşturarak üst düzey sistem tasarımını ve amaçlanan bağımlılıklarını tanıtın. Koddaki bağımlılıkların tasarımla tutarlı kalmasını sağlamak için kodu bu tasarıma karşı doğrulayın.|- [Kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analiz ve model mimarisi](../modeling/analyze-and-model-your-architecture.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
