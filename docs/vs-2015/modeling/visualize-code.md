---
title: Kodu görselleştirin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 665dc76126eac964f405be06605c40b5b30cc9a5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532944"
---
# <a name="visualize-code"></a>Kodu görselleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da görselleştirme ve modelleme araçlarını kullanarak mevcut kodu anlamanıza ve uygulamanızı açıklamanıza yardımcı olabilirsiniz. Bu, değişikliklerinizin kodu nasıl etkileyebileceğini görsel olarak öğrenmenize ve bu değişikliklerden kaynaklanan iş ve riskleri değerlendirmenize yardımcı olur. Örneğin:

- Kodunuzdaki ilişkileri anlamak için, bu ilişkileri görsel olarak eşleyin.

- Sisteminizin mimarisini betimleyip kodu tasarımla tutarlı tutun, katman diyagramları oluşturun ve bu diyagramlarda kodu doğrulayın.

- Sınıf yapılarını anlatmak için sınıf diyagramları oluşturun.

- Sistemin çeşitli yönlerini modellemek ve iletmek için Birleşik Modelleme Dili (UML) diyagramları çizin. Örneğin, bir sistemin bileşenlerini, türlerini, etkileşimlerini ve süreçlerini modelleyebilirsiniz.

  Bu araçlar, projenize dahil olan insanlarla daha kolay iletişim kurmanıza de yardımcı olur. Örneğin, proje hissedarları, kullanıcılar ve takım üyeleri ile sisteme tartışmak için ortak bir sözlük oluşturmak üzere UML sınıf diyagramlarını kullanabilirsiniz.

  Hangi Visual Studio sürümlerini her bir özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|Senaryo|Makaleler|
|-|-|
|**Kodu ve ilişkilerini anlayın:**<br /><br /> Belirli kod parçaları arasındaki ilişkileri eşleyin.<br /><br /> Tüm çözüm için kodunuzdaki ilişkilere genel bakış bölümüne bakın.<br /><br /> **Note**: Bu Visual Studio sürümünde, *bağımlılık grafiğinin*yerine *kod eşleme* terimi kullanılır.|-   [Çözümleriniz genelinde bağımlılıkları eşleyin](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanın](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Kod Haritası Çözümleyicileri kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Sınıf yapılarını anlayın:**<br /><br /> Koddan sınıf diyagramları oluşturarak bir projedeki sınıfların yapısını görselleştirin.|[Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Üst düzey sistem tasarımını açıkla ve kodu bu tasarıma göre doğrula:**<br /><br /> Katman diyagramları oluşturarak üst düzey sistem tasarımını ve amaçlanan bağımlılıklarını tanıtın. Koddaki bağımlılıkların tasarımla tutarlı kalmasını sağlamak için kodu bu tasarıma karşı doğrulayın.|-   [Kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Katman diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|
|**Kullanıcı gereksinimlerini ve mimarisini iletişim kurun:**<br /><br /> Aşağıdaki UML diyagramlarını çizerek yazılım sisteminizin Kullanıcı gereksinimlerini ve mimarisini modelleyin: etkinlik, bileşen, sınıf, sıra ve kullanım örneği.|-   [Uygulamanız için modeller oluşturma](../modeling/create-models-for-your-app.md)<br />-   [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)<br />-   [Uygulamanızın mimarisini modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|------------------|---------------|
|**Forumlar**|-   [Visual Studio görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio görselleştirme & modelleme SDK (DSL araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Bloglar**|[Visual Studio ALM + Team Foundation Server blogu](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Teknik makaleler ve Günlükler**|[MSDN mimarisi Forumu](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Ayrıca Bkz.
 [Senaryo: görselleştirme ve modelleme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [çözümleme ve modelleme mimarisini](../modeling/analyze-and-model-your-architecture.md) kullanarak tasarımınızı değiştirme [uygulama modelinize yönelik modeller oluşturma](../modeling/create-models-for-your-app.md) [Kullanıcı gereksinimleri](../modeling/model-user-requirements.md) [modeli](../modeling/model-your-app-s-architecture.md) [geliştirme sürecinizdeki uygulamanızın mimarisi kullanım modelleri](../modeling/use-models-in-your-development-process.md)
