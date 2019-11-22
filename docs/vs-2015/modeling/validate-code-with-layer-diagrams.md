---
title: Katman diyagramları ile kodu doğrulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 596711c5c59738d5356437bb761e80caeddfbd6b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301350"
---
# <a name="validate-code-with-layer-diagrams"></a>Katman diyagramları ile kod doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodun tasarımıyla çakışmadığından emin olmak için, Visual Studio 'daki katman diyagramlarıyla kodunuzu doğrulayın. Bu, şu konularda size yardımcı olabilir:

- Kodunuzdaki ve katman diyagramındaki bağımlılıklar arasında çakışmaları bulun.

- Önerilen değişiklikler tarafından etkilenebilecek bağımlılıkları bulun.

   Örneğin, olası mimari değişiklikleri göstermek için katman diyagramını düzenleyebilir ve ardından etkilenen bağımlılıkları görmek için kodu doğrulayabilirsiniz.

- Kodu yeniden düzenleyin veya kodu farklı bir tasarıma geçirin.

   Kodu farklı bir mimariye taşıdığınız zaman iş gerektiren kodu veya bağımlılıkları bulun.

  **Gereksinimler**

- Visual Studio

- Team Foundation yapısı ile kodu otomatik olarak doğrulamak için Team Foundation Yapı sunucunuzdaki Visual Studio

- Katman diyagramına sahip bir modelleme projesi olan çözüm. Bu katman diyagramı, doğrulamak istediğiniz Visual C# .NET veya Visual Basic .NET projelerindeki yapılara bağlı olmalıdır. Bkz. [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).

  Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Visual Studio'daki açık bir katman diyagramından veya komut isteminden kodu el ile doğrulayabilirsiniz. Ayrıca yerel yapıları veya Team Foundation Yapısı'nı çalıştırırken kodu otomatik olarak doğrulayabilirsiniz. Bkz. [Channel 9 video: Katman diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama](https://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Katman doğrulamasını Team Foundation yapısı ile çalıştırmak istiyorsanız, Yapı sunucunuza aynı Visual Studio sürümünü de yüklemelisiniz.

- [Bir öğenin doğrulamayı destekleyip desteklemediğini görün](#SupportsValidation)

- [Doğrulama için diğer .NET derlemelerini ve projelerini ekleyin](#IncludeReferences)

- [Kodu el ile doğrulama](#ValidateManually)

- [Kodu otomatik olarak doğrula](#ValidateAuto)

- [Katman doğrulama sorunlarını giderme](#TroubleshootingValidation)

- [Katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a>Bir öğenin doğrulamayı destekleyip desteklemediğini görün
 Katmanları Web sitelerine, Office belgelerine, düz metin dosyalarına ve birden çok uygulama arasında paylaşılan projelerdeki dosyalara bağlayabilirsiniz, ancak doğrulama işlemi bunları içermez. Doğrulama hataları, aralarında hiçbir bağımlılığın görünmediği ayrı katmanlara bağlanmış projelere veya derlemelere olan başvurular için görünmez. Kod bu başvuruları kullanmazsa böyle başvurular bağımlılık olarak düşünülmez.

1. Katman diyagramında bir veya daha fazla katman seçin, seçiminize sağ tıklayın ve **bağlantıları görüntüle**' ye tıklayın.

2. **Katman Gezgini**' nde **doğrulamayı destekler** sütununa bakın. Değer false ise, öğe doğrulamayı desteklemez.

## <a name="IncludeReferences"></a>Doğrulama için diğer .NET derlemelerini ve projelerini ekleyin
 Öğeleri katman diyagramına sürüklediğinizde, karşılık gelen .NET derlemelerine veya projelere başvurular, modelleme projesindeki **Katman başvuruları** klasörüne otomatik olarak eklenir. Bu klasör, doğrulama sırasında analiz edilen derlemeler ve projeler için başvurular içerir. Ayrıca, diğer .NET derlemelerini ve projeleri katman diyagramına el ile sürüklemeden doğrulama için ekleyebilirsiniz.

1. **Çözüm Gezgini**, modelleme projesine veya **Katman başvuruları** klasörüne sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda derlemeler veya projeler ' i seçin ve ardından **Tamam**' a tıklayın.

## <a name="ValidateManually"></a>Kodu el ile doğrulama
 Çözüm öğeleriyle bağlantılı bir açık katman diyagramı varsa, diyagramdaki kısayolu **Doğrula** komutunu çalıştırabilirsiniz. Ayrıca, **/p: ValidateArchitecture** özel özelliği **true**olarak ayarlanmış şekilde **MSBuild** komutunu çalıştırmak için komut istemi ' ni de kullanabilirsiniz. Örneğin, kodda değişiklik yaparken bağımlılık çakışmalarını önceden yakalayabilmek için düzenli olarak katman doğrulama gerçekleştirin.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Kodu açık bir katman diyagramından doğrulamak için

1. Diyagram yüzeyine sağ tıklayın ve sonra **Mimariyi Doğrula**' ya tıklayın.

    > [!NOTE]
    > Varsayılan olarak, katman diyagramı (. layerdiagram) dosyasındaki **derleme eylemi** özelliği, diyagramın doğrulama işlemine dahil edilmesini sağlamak üzere **doğrulanacak** şekilde ayarlanır.

     **Hata listesi** penceresi oluşan tüm hataları bildirir. Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).

2. Her bir hatanın kaynağını görüntülemek için **hata listesi** penceresindeki hataya çift tıklayın.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], hatanın kaynağı yerine bir kod Haritası gösterebilir. Bu, kodun katman diyagramı tarafından belirlenmeyen derlemesinde bağımlılığı varsa ya da kodun katman diyagramı tarafından belirlenen bağımlılığı eksikse ortaya çıkar. Bağımlılığın var olup olmayacağını öğrenmek için kod haritasını veya kodu gözden geçirin. Kod eşlemeleri hakkında daha fazla bilgi için bkz. [çözümlerinizi genelinde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

3. Hataları yönetmek için bkz. [doğrulama hatalarını yönetme](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Kodu komut isteminde doğrulamak için

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komut istemi ' ni açın.

2. Aşağıdakilerden birini seçin:

   - Çözümdeki belirli bir modelleme projesine yönelik kodu doğrulamak için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aşağıdaki özel özellik ile çalıştırın.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - veya -

       Modelleme projesi (. modelproj) dosyasını ve katman diyagramını içeren klasöre gidin ve aşağıdaki özel özellikle [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çalıştırın:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Kodu Çözümdeki tüm modelleme projelerine karşı doğrulamak için aşağıdaki özel özellikle [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çalıştırın:

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - veya -

       Bir katman diyagramı içeren modelleme projesi içermesi gereken çözüm klasörüne gidin ve aşağıdaki özel özellikle [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çalıştırın:

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Oluşan hatalar listelenecektir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]hakkında daha fazla bilgi için bkz. [MSBuild](../msbuild/msbuild.md) ve [MSBuild görevi](../msbuild/msbuild-task.md).

   Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a>Doğrulama hatalarını yönetme
 Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdığınızda, [!INCLUDE[esprfound](../includes/esprfound-md.md)]bir iş öğesini günlüğe kaydetmek iyi bir uygulamadır.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bu öğeye bağlanmak için TFS kaynak kodu denetimine (SCC) zaten bağlanmış olmanız gerekir. Farklı bir TFS SCC bağlantısını açmaya çalışırsanız, Visual Studio geçerli çözümü otomatik olarak kapatır. Bir iş öğesini oluşturmayı veya bir iş öğesini bağlamayı denemeden önce uygun SCC 'e zaten bağlı olduğunuzdan emin olun. Visual Studio 'nun sonraki sürümlerinde, bir SCC 'e bağlı değilseniz menü komutları kullanılamaz.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Doğrulama hatası için bir öğesi oluşturmak üzere

- **Hata listesi** penceresinde, hataya sağ tıklayın, **iş öğesi oluştur**' un üzerine gelin ve sonra oluşturmak istediğiniz iş öğesi türüne tıklayın.

  **Hata listesi** penceresindeki doğrulama hatalarını yönetmek için bu görevleri kullanın:

|**To**|**Bu adımları izleyin**|
|------------|----------------------------|
|Doğrulama sırasında seçili hataları gizleme|Seçilen bir veya birden çok hataya sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından **hataları Gizle**' ye tıklayın.<br /><br /> Gizlenen hatalar üstü çizili biçimde görünür. Doğrulamayı daha sonra çalıştırdığınızda bu hatalar görünmez.<br /><br /> Gizlenen hatalar, ilgili katman diyagramı dosyası için .gizlenenler dosyasında izlenir.|
|Seçili hataların gizlenmesini durdurma|Seçili gizlenen hata veya hatalara sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından hataları gizlemeyi **Durdur**' a tıklayın.<br /><br /> Doğrulamayı daha sonra çalıştırdığınızda seçili gizlenen hatalar görünecektir.|
|Tüm gizlenen hataları **hata listesi** penceresinde geri yükle|**Hata listesi** penceresinde herhangi bir yere sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından **Tüm gizlenen hataları göster**' e tıklayın.|
|**Hata listesi** penceresinden gizlenen tüm hataları gizle|**Hata listesi** penceresinde herhangi bir yere sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından **Tüm gizlenen hataları Gizle**' ye tıklayın.|

## <a name="ValidateAuto"></a>Kodu otomatik olarak doğrula
 Her yerel bir yapı çalıştırışınızda katman doğrulama gerçekleştirebilirsiniz. Takınınız Team Foundation Yapısı kullanıyorsa, özel bir MSBuild görevi oluşturarak belirtebileceğiniz geçitli iadelerle katman doğrulaması gerçekleştirebilir ve doğrulama hatalarını toplamak için yapı raporları kullanabilirsiniz. Geçitli iade derlemeleri oluşturmak için bkz. [değişiklikleri doğrulamak için geçitli iade derleme Işlemi kullanma](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Kodu yerel yapı sırasında otomatik olarak doğrulamak için

- Modelleme projesi (.modelproj) dosyası açmak için metin düzenleyicisi kullanın ve ardından aşağıdaki özelliği ekleyin:

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- veya -

1. **Çözüm Gezgini**, katman diyagramını veya diyagramlarını içeren modelleme projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellikler** penceresinde, modelleme projesinin **Mimariyi Doğrula** özelliğini **doğru**olarak ayarlayın.

    Bu, doğrulama işlemi içinde modelleme projesini içerir.

3. **Çözüm Gezgini**, doğrulama için kullanmak istediğiniz katman diyagramı (. layerdiagram) dosyasına tıklayın.

4. **Özellikler** penceresinde diyagramın **Build Action** özelliğinin **Validate**olarak ayarlandığından emin olun.

    Buna, doğrulama işlemindeki katman diyagramı dahildir.

   Hata Listesi penceresindeki hataları yönetmek için bkz. [doğrulama hatalarını yönetme](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Kodu Team Foundation Yapısı sırasında otomatik olarak doğrulamak için

1. **Takım Gezgini**, derleme tanımına çift tıklayın ve ardından **işlem**' e tıklayın.

2. **Yapı işlemi parametreleri**altında, **derleme**' yı genişletin ve **MSBuild bağımsız değişkenleri** parametresine aşağıdakini yazın:

    `/p:ValidateArchitecture=true`

   Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors). [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]hakkında daha fazla bilgi için bkz.:

- [Uygulamayı oluşturun](/azure/devops/pipelines/index)

- [Yapı işleminiz için varsayılan şablonu kullanın](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [UpgradeTemplate. xaml ' i temel alan eski bir derlemeyi değiştirme](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Yapı işlemi şablonunuzu özelleştirme](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Çalışan bir yapı için Ilerlemeyi izleme](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a>Katman doğrulama sorunlarını giderme
 Aşağıdaki tabloda katman doğrulama sorunları ve bunların çözümü açıklanmaktadır. Bu sorunlar, kod ve tasarım arasındaki çakışmalarla sonuçlanan hatalardan ayrılır. Bu hatalar hakkında daha fazla bilgi için bkz. [katman doğrulama hatalarını anlama ve çözme](#UnderstandingValidationErrors).

|**Konuda**|**Olası neden**|**Çözümleme**|
|---------------|------------------------|--------------------|
|Doğrulama hataları beklendiği gibi gerçekleşmez.|Doğrulama Çözüm Gezgini'ndeki diğer katman diyagramlarından kopyalanmış ve aynı modelleme projesinde bulunan katman diyagramlarında işe yaramaz. Bu şekilde kopyalanan katman diyagramları, orijinal katman diyagramıyla aynı başvuruları içerir.|Modelleme projesine yeni bir katman diyagramı ekleyin.<br /><br /> Öğeleri kaynak katmanı diyagramından yeni diyagrama kopyalayın.|

## <a name="UnderstandingValidationErrors"></a>Katman doğrulama hatalarını anlama ve çözme
 Kodu katman diyagramına karşı doğruladığınız zaman, kod tasarımla çakıştığında doğrulama hataları oluşur. Örneğin, aşağıdaki durumlar doğrulama hatalarının oluşmasına neden olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

  Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu görevi yinelemeli bir şekilde gerçekleştirebilirsiniz.

  Aşağıdaki bölümde, bu hatalarda kullanılan sözdizimi belirtilmekte, bu hataların anlamı açıklanmakta ve bunları çözmek veya yönetmek için yapabilecekleriniz önerilmektedir.

|**Söz dizimi**|**Açıklama**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* katman diyagramındaki bir katmanla ilişkili bir yapıdır.<br /><br /> *ArtifactTypeN* , bir **sınıf** veya **Yöntem**gibi *ArtifactN*türüdür, örneğin:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Bir ad alanının adı.|
|*Layernamence*|Katman diyagramındaki katmanın adı.|
|*DependencyType*|*Artifact1* ve *Artifact2*arasındaki bağımlılık ilişkisinin türü. Örneğin, *Artifact1* , *Artifact2*ile bir **çağrı** ilişkisine sahiptir.|

|**Hata sözdizimi**|**Hata açıklaması**|
|----------------------|---------------------------|
|AV0001: geçersiz bağımlılık: *Artifact1*(*ArtifactType1*)--> *Artifact2*(*ArtifactType2*)<br /><br /> Katmanlar: *LayerName1 & lt*, *LayerName2* &#124; Bağımlılıklar: *dependencyType*|*Layername1 & lt* *LayerName2*üzerinde doğrudan bağımlılığı olmadığından *LayerName1 & lt* içindeki *Artifact1* , *LayerName2* içindeki *Artifact2* bağımlılığı içermemelidir.|
|AV1001: geçersiz ad alanı: *yapıt*<br /><br /> Katman: *LayerName* &#124; gereken ad alanı: *NamespaceName1* &#124; geçerli ad alanı: *NamespaceName2*|*LayerName* , ilişkili yapıtların *NamespaceName1*'e ait olması gerekir. *Yapıt* , *NamespaceName1*değil *NamespaceName2*' dir.|
|AV1002: yasak ad alanına bağlıdır: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Katman: *LayerName* &#124; yasak ad alanı: *NamespaceName* &#124; bağımlılıkları: *dependencyType*|*LayerName* , ilişkili yapıtların *NamespaceName*'e bağlı olmaması gerekir. *Artifact2* *NamespaceName*içinde olduğu için *Artifact1* , *Artifact2* öğesine bağımlı olamaz.|
|AV1003: yasak ad alanında: *yapıt*(*ArtifactType*)<br /><br /> Katman: *LayerName* &#124; yasak ad alanı: *NamespaceName*|*LayerName* , ilişkili yapıtların *NamespaceName*'e ait olmasını gerektirir. *Yapıt* *NamespaceName*'e aittir.|
|AV3001: eksik bağlantı: '*LayerName*' katmanı bulunamayan '*yapıt*' öğesine bağlanır. Eksik bir derleme başvurunuz mu var?|*LayerName* , bulunamayan bir yapıya bağlantı sağlar. Örneğin, sınıfla kurulan bir bağlantı kayıp olabilir; çünkü modelleme projesinde sınıfı içeren derlemeye yapılan bir başvuru yoktur.|
|AV9001: Mimari çözümleme iç hatalar buldu. Sonuçlar tamamlanmamış olabilir. Daha fazla bilgi için ayrıntılı yapı olay günlüğü veya çıkış penceresine bakın.|Daha fazla ayrıntı için yapı olay günlüğü veya çıkış penceresine bakın.|

## <a name="security"></a>Güvenlik

## <a name="see-also"></a>Ayrıca Bkz.
 [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
