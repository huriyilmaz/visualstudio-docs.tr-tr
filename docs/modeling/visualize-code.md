---
title: Kodu görselleştirme
description: Mevcut kodu anlamak ve uygulamanızı açıklamak için Visual Studio görselleştirme ve modelleme araçlarını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90c180bf9d910227013c2e089001ce5332cd1bd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388353"
---
# <a name="visualize-code"></a>Kodu görselleştirme

Mevcut kodu anlamanıza ve uygulamanızı açıklamanıza yardımcı Visual Studio görselleştirme ve modelleme araçlarını kullanabilirsiniz. Bu, değişikliklerinizin kodu nasıl etkileyeceğini görsel olarak öğrenmenize ve bu değişikliklerden elde edilen iş ve riskleri değerlendirmenize yardımcı olur. Örneğin:

- Kodundaki ilişkileri anlamak için bu ilişkileri görsel olarak eşler.

- Sistem mimarinizi açıklamak ve kodu tasarımıyla tutarlı tutmak için bağımlılık diyagramları oluşturun ve kodu bu diyagramlara göre doğrular.

- Sınıf yapılarını açıklamak için sınıf diyagramları oluşturun.

Bu araçlar ayrıca projenize dahil olan kişiler ile daha kolay iletişim kurmanıza da yardımcı olur.

Her özelliği destekleyen Visual Studio için bkz. Mimari ve modelleme [araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|Senaryo|Makaleler|
|-|-|
|**Kodu ve ilişkilerini anlama:**<br /><br /> Belirli kod parçaları arasındaki ilişkileri eşleme.<br /><br /> Çözümün tamamı için kodundaki ilişkilere genel bakışa bakın.|- [Çözümleriniz genelinde bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />- [Uygulamalarda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Kod eşleme çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Hata ayıklama sırasında çağrı yığınında yöntemleri eşleme](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Sınıf yapılarını anlama:**<br /><br /> Koddan sınıf diyagramları oluşturarak proje içinde sınıfların yapısını görselleştirin.|[Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Üst düzey sistem tasarımını açıklama ve kodu bu tasarıma göre doğrulama:**<br /><br /> Bağımlılık diyagramları oluşturarak üst düzey sistem tasarımını ve hedeflenen bağımlılıklarını açıklama. Kodda bağımlılıkların tasarımla tutarlı kalmasını sağlamak için kodu bu tasarıma göre doğrular.|- [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Mimari kod araçlarını yükleme](install-architecture-tools.md)
- [Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Mimariyi Analiz Etme ve Modelleme](../modeling/analyze-and-model-your-architecture.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
