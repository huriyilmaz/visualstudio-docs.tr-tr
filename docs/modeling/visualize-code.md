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
ms.openlocfilehash: 56b938321c2b6d1161052ac2358547d72a6bf4e7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593999"
---
# <a name="visualize-code"></a>Kodu görselleştirme

Visual Studio 'da görselleştirme ve modelleme araçlarını kullanarak mevcut kodu anlamanıza ve uygulamanızı açıklamanıza yardımcı olabilirsiniz. Bu sayede değişikliklerinizin kodunuzu nasıl etkileyeceğini görsel olarak öğrenebilir ve söz konusu değişiklikler sonucu ortaya çıkabilecek riskleri hesaplayabilirsiniz. Örneğin:

- Kodunuzdaki ilişkileri anlamak için, bu ilişkileri görsel olarak eşleyin.

- Sisteminizin mimarisini betimleyip kodu tasarımla tutarlı tutun, bağımlılık diyagramları oluşturun ve kodu bu diyagramlarda doğrulayın.

- Sınıf yapılarını anlatmak için sınıf diyagramları oluşturun.

Bu araçlar, projenize dahil olan insanlarla daha kolay iletişim kurmanıza de yardımcı olur.

Hangi Visual Studio sürümlerini her bir özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|||
|-|-|
|**Kodu ve ilişkilerini anlayın:**<br /><br /> Belirli kod parçaları arasındaki ilişkileri eşleyin.<br /><br /> Tüm çözüm için kodunuzdaki ilişkilere genel bakış bölümüne bakın.|[çözümlerinizin genelinde harita bağımlılıklarını](../modeling/map-dependencies-across-your-solutions.md) - <br />[uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanın](../modeling/use-code-maps-to-debug-your-applications.md) - <br />- [kod Haritası Çözümleyicileri kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />[hata ayıklarken çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) - |
|**Sınıf yapılarını anlayın:**<br /><br /> Koddan sınıf diyagramları oluşturarak bir projedeki sınıfların yapısını görselleştirin.|[Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Üst düzey sistem tasarımını açıkla ve kodu bu tasarıma göre doğrula:**<br /><br /> Bağımlılık diyagramları oluşturarak üst düzey sistem tasarımını ve amaçlanan bağımlılıklarını tanıtın. Koddaki bağımlılıkların tasarımla tutarlı kalmasını sağlamak için kodu bu tasarıma karşı doğrulayın.|- [kodınızdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />[bağımlılık diyagramlarında kodu doğrulamak](../modeling/validate-code-with-layer-diagrams.md) - |

## <a name="see-also"></a>Ayrıca bkz.

- [Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analiz ve model mimarisi](../modeling/analyze-and-model-your-architecture.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
