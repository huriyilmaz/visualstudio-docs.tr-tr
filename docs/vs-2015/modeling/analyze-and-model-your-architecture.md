---
title: Mimarinizi çözümleyin ve modelleyin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a505cd9fd40a47c58135506cf7e022409e9b77e
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852069"
---
# <a name="analyze-and-model-your-architecture"></a>Mimarinizi çözümleme ve mimarinizin modelini oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı tasarlamak ve modellemek için Visual Studio mimarisi ve modelleme araçlarını kullanarak uygulamanızın kullanıcı gereksinimlerini karşıladığından emin olun. Kodun yapısını, davranışını ve ilişkilerini görselleştirmek için Visual Studio kullanarak mevcut program kodunu daha kolay bir şekilde anlayın.

 Geliştirme sürecinizin bir parçası olarak uygulama yaşam döngüsü boyunca farklı ayrıntı düzeylerinde modeller oluşturun. Model öğelerini Team Foundation Server iş öğelerine ve geliştirme planınıza bağlayarak modelleriniz ile ilişkili gereksinimleri, görevleri, test çalışmalarını, hataları ve diğer işleri izleyin. Bkz. [Senaryo: görselleştirme ve modelleme kullanarak tasarımınızı değiştirme](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Hangi Visual Studio sürümlerini her bir özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="to"></a>Bitiş

|||
|-|-|
|**Kodu görselleştirin**:<br /><br /> -Kod haritaları oluşturarak kodun kuruluşuna ve ilişkilerine bakın. Derlemeler, ad alanları, sınıflar, yöntemler vb. arasındaki bağımlılıkları görselleştirin.<br />-Koddan sınıf diyagramları oluşturarak belirli bir proje için sınıf yapısına ve üyelere bakın.<br />-Kodu doğrulamak için katman diyagramları oluşturarak kodunuz ve tasarımı arasında çakışmalar bulun.<br /><br /> **Note**: Bu Visual Studio sürümünde, *bağımlılık grafiğinin*yerine *kod eşleme* terimi kullanılır. Tek başına *kullanıldığında oluşan terimi* genellikle bir yönlendirilmiş GRAFIĞE veya dgml diyagramına (veya belgeye) başvurur. Kod eşlemeleri, özel bir DGML diyagramı türüdür.|[Kodu görselleştirme](../modeling/visualize-code.md) -   <br />[sınıflarla ve diğer türlerle çalışma -   (sınıf Tasarımcısı)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [videosu: görselleştirme aracılığıyla kod bağımlılıklarınızı anlama (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)<br />-   [videosu: bir değişikliğin etkisini görselleştirin (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)|
|**Kullanıcı gereksinimlerini açıkla ve iletişim kurma**:<br /><br /> -Kullanıcı hikayelerini, iş kurallarını ve diğer gereksinimleri açıklığa kavuşturun ve kullanım örneği, etkinlik ve sınıf diyagramları gibi UML diyagramları çizerek tutarlılığının sağlanmasına yardımcı olun.|[uygulamanız için modeller oluşturma](../modeling/create-models-for-your-app.md) -   <br />-   [modeli kullanıcı gereksinimleri](../modeling/model-user-requirements.md)<br />-   [video: modelleme aracılığıyla mimariyi geliştirme (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)|
|**Mimariyi tanımlayın**:<br /><br /> -UML bileşeni, sınıf ve sıralı diyagramlar çizerek yazılım sisteminizin büyük ölçekli yapısını ve tasarım düzenlerini modelleyin.<br />-Katman diyagramları oluşturarak kodunuzun bileşenleri arasındaki bağımlılıklar için kısıtlamalar tanımlayın ve uygulayın.|[uygulamanız için modeller oluşturma](../modeling/create-models-for-your-app.md) -   <br />[uygulamanızın mimarisine -   modeli](../modeling/model-your-app-s-architecture.md)<br />-   [video: modelleme aracılığıyla mimariyi geliştirme (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)<br />-   [video: mimarinizi tasarlamak ve doğrulamak için katman diyagramlarını kullanma (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Gereksinimleri ve hedeflenen tasarımı kullanarak sisteminizi doğrulayın:**<br /><br /> -Kabul testlerini veya sistem testlerini, gereksinim modellerine göre tanımlayın. Bu, testler ve kullanıcılarınızın gereksinimleri arasında güçlü bir ilişki oluşturur ve gereksinimler değiştiğinde sistemi daha kolay bir şekilde güncelleştirmenize yardımcı olur.<br />-Hedeflenen mimariyi tanımlayan ve tasarımla çakışabilecek değişiklikleri önleyen katman diyagramlarıyla kod bağımlılıklarını doğrulayın.|[geliştirme sırasında sisteminizi doğrulamak](../modeling/validate-your-system-during-development.md) -   <br />-   [video: mimarinizi tasarlamak ve doğrulamak için katman diyagramlarını kullanma (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Team Foundation sürüm denetimi 'ni kullanarak modelleri, diyagramları ve kod eşlemelerini paylaşma**:<br /><br /> -Bunları paylaşmak için, Team Foundation sürüm denetimi altına kod haritaları, modelleme projeleri, UML diyagramları ve katman diyagramları koyun.|Team Foundation sürüm denetimi altında bu öğelerle çalışan birden fazla kullanıcınız varsa, sürüm denetimi sorunlarından kaçınmanıza yardımcı olması için bu yönergeleri kullanın:<br /><br /> [sürüm denetimi altındaki modelleri ve diyagramları yönetmek](../modeling/manage-models-and-diagrams-under-version-control.md) -   |
|**UML veya etki alanına özgü dillerden uygulamanızın parçalarını oluşturun veya yapılandırın**:<br /><br /> -Tasarımınızın, gereksinim değişikliklerine ve bir ürün hattında kolayca değişkene daha hızlı yanıt vermesini sağlayın.|[uygulamanızı modellerden oluşturma ve yapılandırma](../modeling/generate-and-configure-your-app-from-models.md) -   |
|**Modelleri ve diyagramları özelleştirme**:<br /><br /> -Modelleri, modellerinizin iş kurallarınıza uygun olduğundan emin olmak için doğrulama kısıtlamaları, UML öğeleri için ek özellikler tanımlayarak ve ek menü komutları ve araç kutusu öğeleri için modelleyerek projenizin bunları nasıl kullandığına uyarlayabilirsiniz.<br />-Kendi etki alanına özgü dillerinizi oluşturun.|[UML modellerini ve diyagramlarını genişletmek](../modeling/extend-uml-models-and-diagrams.md) -   <br />[Visual Studio için -   modelleme SDK 'sı-etki alanına özgü diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**T4 şablonlarını kullanarak metin oluştur**:<br /><br /> -Metin tabanlı dosyalar oluşturmak için şablonlar içindeki metin bloklarını ve denetim mantığını kullanın.|-   [kod üretimi ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Model türleri ve kullanımları

|**Model türü ve tipik kullanımları**|
|-------------------------------------|
|**Kod haritaları**<br /><br /> Kod haritaları kodunuzda organizasyonu ve ilişkileri görmenizi de yardımcı olur.<br /><br /> Tipik kullanımlar:<br /><br /> -Program kodunu, yapısını ve bağımlılıklarını daha iyi anlamak, güncelleştirmeyi güncelleştirmek ve önerilen değişikliklerin maliyetini tahmin etmek için inceleyin.<br /><br /> Bkz.<br /><br /> [çözümlerinizin genelinde harita bağımlılıklarını](../modeling/map-dependencies-across-your-solutions.md) -   <br />[uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanın](../modeling/use-code-maps-to-debug-your-applications.md) -   <br />-   [kod Haritası Çözümleyicileri kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Katman diyagramı**<br /><br /> Katman diyagramları, bir uygulamanın yapısını açık bağımlılıklara sahip bir katman veya blok kümesi olarak tanımlamanızı sağlar. Bir katman diyagramında açıklanan koddaki ve bağımlılıklarda bağımlılıklar arasındaki çakışmaları saptamak için doğrulamayı çalıştırabilirsiniz.<br /><br /> Tipik kullanımlar:<br /><br /> -Uygulamanın yapısını ömrü boyunca çok sayıda değişiklikle sabitleştir.<br />-Koda yapılan değişiklikleri iade etmeden önce istemeden bağımlılık çakışmalarını bulun.<br /><br /> Bkz.<br /><br /> -   [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />[Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md) -   |
|**UML modeli**<br /><br /> UML modeli, sınıf, bileşen, kullanım örneği, etkinlik ve sıralı diyagramlar dahil olmak üzere çeşitli görünümler içerir. UML uygulamasını uygulama etki alanına uyacak şekilde özelleştirebilirsiniz. Örneğin, model öğelerine etiketler, ek bilgiler ve kısıtlamalar ekleyebilirsiniz. Modeller üzerinde çalışan araçlar da tanımlayabilirsiniz. Bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).<br /><br /> Tipik kullanımlar:<br /><br /> -Gereksinimleri ve tasarımı tanıtın. UML uygulamasını herhangi bir uygulamanın geliştirmesine hızlıca uygulayabilirsiniz. Bkz. [geliştirme sürecinizdeki modelleri kullanma](../modeling/use-models-in-your-development-process.md).<br />-Testleri veya bir uygulamanın parçalarını oluşturun veya yapılandırın. Gösterimi özelleştirmek ve oluşturma şablonlarını veya yapılandırılabilir uygulamayı geliştirmek için bazı işler gereklidir. Bkz. [uygulamanızı modellerden oluşturma ve yapılandırma](../modeling/generate-and-configure-your-app-from-models.md).<br />-Genel açıklama ve kod oluşturma veya daha küçük projelerde yapılandırma için.|
|**Etki alanına özgü dil (DSL)**<br /><br /> DSL, belirli bir amaç için tasarladığınız bir gösterimidir. Visual Studio 'da genellikle grafik olur.<br /><br /> Tipik kullanımlar:<br /><br /> -Uygulamanın parçalarını oluşturun veya yapılandırın. Gösterimi ve araçları geliştirmek için çalışma gerekir. Sonuç, UML özelleştirmesinden daha iyi bir şekilde etki alanına uygun olabilir.<br />-Büyük projeler veya DSL ve araçları geliştirmedeki yatırımın birden fazla projede kullanımı tarafından döndürüldüğü ürün hatları için.<br /><br /> Bkz.<br /><br /> [Visual Studio için -   modelleme SDK 'sı-etki alanına özgü diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?

|||
|-|-|
|**Forumlar**|-   [Visual Studio görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio görselleştirme & modelleme SDK (dsl araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio 2015 ' de modellemeye yönelik yenilikler](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps ve uygulama yaşam döngüsü yönetimi](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
