---
title: Bağımlılık diyagramları ile kod doğrulama
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fc852b4d5003cf809248c72ca3ac42ad3a6bf23
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981127"
---
# <a name="validate-code-with-dependency-diagrams"></a>Bağımlılık diyagramları ile kod doğrulama

## <a name="why-use-dependency-diagrams"></a>Bağımlılık diyagramları neden kullanılmalıdır?

Kodun tasarımıyla çakışmadığından emin olmak için, Visual Studio 'da bağımlılık diyagramlarıyla kodunuzu doğrulayın. Bu, şu konularda size yardımcı olabilir:

- Kodunuzda bağımlılıklar ve bağımlılık diyagramındaki bağımlılıklarla ilgili çakışmalar bulun.

- Önerilen değişiklikler tarafından etkilenebilecek bağımlılıkları bulun.

   Örneğin, olası mimari değişikliklerini göstermek için bağımlılık diyagramını düzenleyebilir ve ardından etkilenen bağımlılıkları görmek için kodu doğrulayabilirsiniz.

- Kodu yeniden düzenleyin veya kodu farklı bir tasarıma geçirin.

   Kodu farklı bir mimariye taşıdığınız zaman iş gerektiren kodu veya bağımlılıkları bulun.

**Requirements**

- Visual Studio

  .NET Core projesi için bir bağımlılık diyagramı oluşturmak için, Visual Studio 2019 sürüm 16,2 veya sonraki bir sürüme sahip olmanız gerekir.

- Bağımlılık diyagramı içeren modelleme projesine sahip bir çözüm. Bu bağımlılık diyagramı, doğrulamak istediğiniz C# veya Visual Basic projelerindeki yapıtlarla bağlantılı olmalıdır. Bkz. [kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).

Hangi Visual Studio sürümlerini bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Kodu, Visual Studio 'da veya bir komut isteminden açık bir bağımlılık diyagramından el ile doğrulayabilirsiniz. Ayrıca, yerel derlemeleri veya Azure Pipelines yapılarını çalıştırırken kodu otomatik olarak doğrulayabilirsiniz. Bkz. [Channel 9 videosu: bağımlılık diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Team Foundation Server (TFS) kullanarak katman doğrulaması çalıştırmak istiyorsanız, Yapı sunucunuza aynı Visual Studio sürümünü de yüklemelisiniz.

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulaması

Bağımlılık doğrulaması gerçek zamanlı olarak gerçekleşir ve hatalar hemen **hata listesi**görüntülenir.

* Ve Visual Basic için C# canlı doğrulama desteklenir.

* Canlı bağımlılık doğrulaması kullanırken tam çözüm analizini etkinleştirmek için, **hata listesi**görüntülenen altın çubuktan seçenekler ayarlarını açın.

  - Çözümünüzde tüm mimari sorunları görmekten ilgileniyorsanız, altın rengi kalıcı olarak kapatabilirsiniz.
  - Tam çözüm analizini etkinleştirmezseniz, analiz yalnızca düzenlenmekte olan dosyalar için yapılır.

* Canlı doğrulamayı etkinleştirmek için projeleri yükseltirken, bir iletişim kutusu dönüştürmenin ilerlemesini gösterir.

* Canlı bağımlılık doğrulaması için bir projeyi güncelleştirirken, NuGet paketinin sürümü tüm projeler için aynı olacak şekilde yükseltilir ve en yüksek sürümdür.

* Yeni bir bağımlılık doğrulama projesi eklemek bir proje güncelleştirmesini tetikler.

## <a name="see-if-an-item-supports-validation"></a>Bir öğenin doğrulamayı destekleyip desteklemediğini görme

Katmanları birden çok uygulama arasında paylaşılan Web sitelerine, Office belgelerine, düz metin dosyalarına ve projelerdeki dosyalara bağlayabilirsiniz, ancak doğrulama işlemi bunları içermez. Doğrulama hataları, aralarında hiçbir bağımlılığın görünmediği ayrı katmanlara bağlanmış projelere veya derlemelere olan başvurular için görünmez. Kod bu başvuruları kullanmazsa böyle başvurular bağımlılık olarak düşünülmez.

1. Bağımlılık diyagramında bir veya daha fazla katman seçin, seçiminize sağ tıklayın ve **bağlantıları görüntüle**' ye tıklayın.

2. **Katman Gezgini**' nde **doğrulamayı destekler** sütununa bakın. Değer false ise, öğe doğrulamayı desteklemez.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Diğer .NET derlemelerini ve projelerini doğrulama için dahil etme

Öğeleri bağımlılık diyagramına sürüklediğinizde, karşılık gelen .NET derlemelerine veya projelerine başvurular, modelleme projesindeki **Katman başvuruları** klasörüne otomatik olarak eklenir. Bu klasör, doğrulama sırasında analiz edilen derlemeler ve projeler için başvurular içerir. Doğrulama için diğer .NET derlemelerini ve projelerini, bunları bağımlılık diyagramına el ile sürüklemeden dahil edebilirsiniz.

1. **Çözüm Gezgini**, modelleme projesine veya **Katman başvuruları** klasörüne sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda derlemeler veya projeler ' i seçin ve ardından **Tamam**' a tıklayın.

## <a name="validate-code-manually"></a>Kodu el ile doğrulama

Çözüm öğelerine bağlı açık bir bağımlılık diyagramınız varsa, diyagramdaki kısayolu **Doğrula** komutunu çalıştırabilirsiniz. Ayrıca, **/p: ValidateArchitecture** özel özelliği **true**olarak ayarlanmış şekilde **MSBuild** komutunu çalıştırmak için komut istemi ' ni de kullanabilirsiniz. Örneğin, kodda değişiklik yaparken bağımlılık çakışmalarını önceden yakalayabilmek için düzenli olarak katman doğrulama gerçekleştirin.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Açık bağımlılık diyagramından kodu doğrulama

1. Diyagram yüzeyine sağ tıklayın ve sonra **Mimariyi Doğrula**' ya tıklayın.

    > [!NOTE]
    > Varsayılan olarak, bağımlılık diyagramı (. layerdiagram) dosyasındaki **derleme eylemi** özelliği, diyagramın doğrulama işlemine dahil edilmesini sağlamak üzere **doğrulanacak** şekilde ayarlanır.

     **Hata listesi** penceresi oluşan tüm hataları bildirir. Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama sorunlarını giderme](#troubleshoot-layer-validation-issues).

2. Her bir hatanın kaynağını görüntülemek için **hata listesi** penceresindeki hataya çift tıklayın.

    > [!NOTE]
    > Visual Studio, hatanın kaynağı yerine bir kod Haritası gösterebilir. Bu, kodun bağımlılık diyagramı tarafından belirtilmeyen bir derlemeye bağımlılığı olduğunda ya da kodda bağımlılık diyagramı tarafından belirtilen bir bağımlılık eksikse oluşur. Bağımlılığın var olup olmayacağını öğrenmek için kod haritasını veya kodu gözden geçirin. Kod eşlemeleri hakkında daha fazla bilgi için bkz. [çözümlerinizi genelinde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

3. Hataları yönetmek için bkz. [katman doğrulama hatalarını çözümleme](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Komut isteminde kodu doğrulama

1. Visual Studio komut istemi 'ni açın.

2. Aşağıdakilerden birini seçin:

   - Çözümdeki belirli bir modelleme projesine yönelik kodu doğrulamak için aşağıdaki özel özellik ile MSBuild 'i çalıştırın.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - veya

       Modelleme projesi (. modelproj) dosyasını ve bağımlılık diyagramını içeren klasöre gidin ve aşağıdaki özel özellikle MSBuild 'i çalıştırın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Çözümdeki tüm modelleme projelerine karşı kodu doğrulamak için aşağıdaki özel özellikle MSBuild 'i çalıştırın:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - veya

       Bağımlılık diyagramı içeren bir modelleme projesi içermesi gereken çözüm klasörüne gidin ve aşağıdaki özel özellikle MSBuild 'i çalıştırın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Oluşan hatalar listelenecektir. MSBuild hakkında daha fazla bilgi için bkz. [MSBuild](../msbuild/msbuild.md) ve [MSBuild görevi](../msbuild/msbuild-task.md).

   Doğrulama hataları hakkında daha fazla bilgi için bkz. [katman doğrulama sorunlarını giderme](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Doğrulama hatalarını yönetme

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdığınızda, bir iş öğesini Team Foundation 'da günlüğe kaydetmek iyi bir uygulamadır.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bu öğeye bağlanmak için TFS kaynak kodu denetimine (SCC) zaten bağlanmış olmanız gerekir. Farklı bir TFS SCC bağlantısını açmaya çalışırsanız, Visual Studio geçerli çözümü otomatik olarak kapatır. Bir iş öğesini oluşturmayı veya bir iş öğesini bağlamayı denemeden önce uygun SCC 'e zaten bağlı olduğunuzdan emin olun. Visual Studio 'nun sonraki sürümlerinde, bir SCC 'e bağlı değilseniz menü komutları kullanılamaz.

#### <a name="create-a-work-item-for-a-validation-error"></a>Doğrulama hatası için bir iş öğesi oluşturma

- **Hata listesi** penceresinde, hataya sağ tıklayın, **iş öğesi oluştur**' un üzerine gelin ve sonra oluşturmak istediğiniz iş öğesi türüne tıklayın.

**Hata listesi** penceresindeki doğrulama hatalarını yönetmek için bu görevleri kullanın:

|**Hedef**|**Bu adımları izleyin**|
|-|-|
|Doğrulama sırasında seçili hataları gizleme|Seçilen bir veya birden çok hataya sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından **hataları Gizle**' ye tıklayın.<br /><br /> Gizlenen hatalar üstü çizili biçimde görünür. Doğrulamayı daha sonra çalıştırdığınızda bu hatalar görünmez.<br /><br /> Gizlenen hatalar, ilgili bağımlılık diyagramı dosyası için bir. suppressions dosyasında izlenir.|
|Seçili hataların gizlenmesini durdurma|Seçili gizlenen hata veya hatalara sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından hataları gizlemeyi **Durdur**' a tıklayın.<br /><br /> Doğrulamayı daha sonra çalıştırdığınızda seçili gizlenen hatalar görünecektir.|
|Tüm gizlenen hataları **hata listesi** penceresinde geri yükle|**Hata listesi** penceresinde herhangi bir yere sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından **Tüm gizlenen hataları göster**' e tıklayın.|
|**Hata listesi** penceresinden gizlenen tüm hataları gizle|**Hata listesi** penceresinde herhangi bir yere sağ tıklayın, **doğrulama hatalarını Yönet**' in üzerine gelin ve ardından **Tüm gizlenen hataları Gizle**' ye tıklayın.|

## <a name="validate-code-automatically"></a>Kodu otomatik olarak doğrulama

Her yerel bir yapı çalıştırışınızda katman doğrulama gerçekleştirebilirsiniz. Takımınız Azure DevOps kullanıyorsa, özel bir MSBuild görevi oluşturarak belirtebileceğiniz ve doğrulama hatalarını toplamak için yapı raporları kullanarak, geçişli iadelerle katman doğrulaması yapabilirsiniz. Geçitli iade derlemeleri oluşturmak için bkz. [TFVC geçitli iade etme](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>Kodu yerel yapı sırasında otomatik olarak doğrulamak için

Modelleme projesi (.modelproj) dosyası açmak için metin düzenleyicisi kullanın ve ardından aşağıdaki özelliği ekleyin:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- veya-

1. **Çözüm Gezgini**' de, bağımlılık diyagramı veya diyagramlarını içeren modelleme projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellikler** penceresinde, modelleme projesinin **Mimariyi Doğrula** özelliğini **doğru**olarak ayarlayın.

    Bu, doğrulama işlemi içinde modelleme projesini içerir.

3. **Çözüm Gezgini**, doğrulama için kullanmak istediğiniz bağımlılık diyagramı (. layerdiagram) dosyasına tıklayın.

4. **Özellikler** penceresinde diyagramın **Build Action** özelliğinin **Validate**olarak ayarlandığından emin olun.

    Bu, doğrulama işlemindeki bağımlılık diyagramını içerir.

Hata Listesi penceresindeki hataları yönetmek için bkz. [katman doğrulama hatalarını çözümleme](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Katman doğrulama sorunlarını giderme

Aşağıdaki tabloda katman doğrulama sorunları ve bunların çözümü açıklanmaktadır. Bu sorunlar, kod ve tasarım arasındaki çakışmalarla sonuçlanan hatalardan ayrılır. Bu hatalar hakkında daha fazla bilgi için bkz. [katman doğrulama sorunlarını giderme](#troubleshoot-layer-validation-issues).

|**Konuda**|**Olası neden**|**Çözünürlüğüne**|
|-|-|-|
|Doğrulama hataları beklendiği gibi gerçekleşmez.|Doğrulama, Çözüm Gezgini ' deki diğer bağımlılık diyagramlarından kopyalanmış ve aynı modelleme projesinde olan bağımlılık diyagramlarında çalışmaz. Bu şekilde kopyalanmış bağımlılık diyagramları, özgün bağımlılık diyagramı ile aynı başvuruları içerir.|Modelleme projesine yeni bir bağımlılık diyagramı ekleyin.<br /><br /> Öğeleri kaynak bağımlılığı diyagramından yeni diyagrama kopyalayın.|

## <a name="resolve-layer-validation-errors"></a>Katman doğrulama hatalarını çözümleme

Kodu bir bağımlılık diyagramına karşı doğruladığınızda, kod tasarımla çakışıyorsa doğrulama hataları oluşur. Örneğin, aşağıdaki durumlar doğrulama hatalarının oluşmasına neden olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu görevi yinelemeli bir şekilde gerçekleştirebilirsiniz.

Aşağıdaki bölümde, bu hatalarda kullanılan sözdizimi belirtilmekte, bu hataların anlamı açıklanmakta ve bunları çözmek veya yönetmek için yapabilecekleriniz önerilmektedir.

|**Sözdizimi**|**Açıklama**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* , bağımlılık diyagramındaki bir katmanla ilişkili bir yapıdır.<br /><br /> *ArtifactTypeN* , bir **sınıf** veya **Yöntem**gibi *ArtifactN*türüdür, örneğin:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Bir ad alanının adı.|
|*Layernamence*|Bağımlılık diyagramındaki bir katmanın adı.|
|*DependencyType*|*Artifact1* ve *Artifact2*arasındaki bağımlılık ilişkisinin türü. Örneğin, *Artifact1* , *Artifact2*ile bir **çağrı** ilişkisine sahiptir.|

| **Hata sözdizimi** | **Hata açıklaması** |
|-|-|
| DV0001: **geçersiz bağımlılık** | Bu sorun, bir katmana eşlenen bir kod öğesi (ad alanı, tür, üye) başka bir katmana eşlenmiş bir kod öğesine başvuruyorsa, ancak bu katmanları içeren bağımlılık doğrulama diyagramında bu katmanlar arasında bağımlılık oku olmadığında raporlanır. Bu bir bağımlılık kısıtlaması ihlalidir. |
| DV1001: **geçersiz ad alanı adı** | Bu sorun, "Izin verilen ad alanı adları" özelliği bu kod öğesinin tanımlandığı ad alanını içermediği bir katmanla ilişkili bir kod öğesinde raporlanır. Bu bir adlandırma kısıtlaması ihlalidir. "Izin verilen ad alanı adları" sözdiziminin, katman olarak ilişkilendirilmiş kod öğelerinin tanımlanmasına izin verilen ad alanlarının noktalı virgülle bir listesi olacağını unutmayın. |
| DV1002: **Referenceable ad alanına bağımlılık** | Bu sorun, katman ile ilişkili bir kod öğesinde raporlanır ve katmanın "Referenceable namespace" özelliğinde tanımlanan bir ad alanında tanımlanan başka bir kod öğesine başvuracaktır. Bu bir adlandırma kısıtlaması ihlalidir. "Başvurulmayan ad alanları" özelliğinin, bu katmanla ilişkili kod öğelerinde başvurulmaması gereken, noktalı virgülle ayrılmış ad alanları listesi olarak tanımlandığını unutmayın. |
| DV1003: **Izin verilmeyen ad alanı adı** | Bu sorun, "Izin verilmeyen ad alanı adları" özelliği bu kod öğesinin tanımlandığı ad alanını içerdiği bir katmanla ilişkili bir kod öğesinde raporlanır. Bu bir adlandırma kısıtlaması ihlalidir. "Izin verilmeyen ad alanı adı" özelliğinin, bu katman ile ilişkili kod öğelerinin tanımlanmadığı ad alanlarının noktalı virgülle ayrılmış bir listesi olarak tanımlandığını unutmayın. |
| DV3001: **eksik bağlantı** | '*LayerName*' katmanı, bulunamayan '*yapıt*' öğesine bağlanır. Eksik bir derleme başvurunuz mu var? |
| DV9001: **mimari analizi iç hatalar buldu** | Sonuçlar tamamlanmamış olabilir. Daha fazla bilgi için ayrıntılı yapı olay günlüğü veya çıkış penceresine bakın. |

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da canlı bağımlılık doğrulaması](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
- [Video: mimari bağımlılıklarınızı gerçek zamanlı olarak doğrulama](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
