---
title: Bağımlılık diyagramları ile kod doğrulama
description: Kodun tasarımıyla çakışmay olduğundan emin olmak için kodunuzu kod içinde bağımlılık diyagramları ile doğrulamanız Visual Studio.
ms.custom: SEO-VS-2020
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 3bb9aeadd0e511ce5ed770eb56f0a2f02bf26542
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123521"
---
# <a name="validate-code-with-dependency-diagrams"></a>Bağımlılık diyagramları ile kod doğrulama

## <a name="why-use-dependency-diagrams"></a>Bağımlılık diyagramlarını neden kullanasınız?

Kodun tasarımıyla çakışmay olduğundan emin olmak için kodunuzu kod içinde bağımlılık diyagramları ile Visual Studio. Bu, şu konularda size yardımcı olabilir:

- Kodundaki bağımlılıklar ve bağımlılık diyagramındaki bağımlılıklar arasındaki çakışmaları bulur.

- Önerilen değişiklikler tarafından etkilenebilecek bağımlılıkları bulun.

   Örneğin, olası mimari değişikliklerini göstermek ve ardından etkilenen bağımlılıkları görmek için kodu doğrulamak için bağımlılık diyagramını düzenleyebilirsiniz.

- Kodu yeniden düzenleyin veya kodu farklı bir tasarıma geçirin.

   Kodu farklı bir mimariye taşıdığınız zaman iş gerektiren kodu veya bağımlılıkları bulun.

**Gereksinimler**

- Visual Studio

  Bir .NET Core projesi için bağımlılık diyagramı oluşturmak için 2019 Visual Studio 16.2 veya sonraki bir sürümüne sahipsiniz.

- Bağımlılık diyagramına sahip modelleme projesine sahip bir çözüm. Bu bağımlılık diyagramı, C# veya doğrulamak istediğiniz Visual Basic yapıtlarla bağlantılı olması gerekir. Bkz. [Kodunuzdan bağımlılık diyagramları oluşturma.](../modeling/create-layer-diagrams-from-your-code.md)

Bu özelliği destekleyen Visual Studio için bkz. Mimari ve [modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

Kodu bir açık bağımlılık diyagramından el ile Visual Studio komut isteminden doğruleyebilirsiniz. Ayrıca yerel derlemeleri veya derlemeleri çalıştırarak kodu Azure Pipelines doğruabilirsiniz. Bkz. [Channel 9 Video: Bağımlılık diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

> [!IMPORTANT]
> Team Foundation Server (TFS) kullanarak katman doğrulama çalıştırmak için derleme sunucunuza aynı Visual Studio yüklemeniz gerekir.

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulaması

Bağımlılık doğrulaması gerçek zamanlı olarak gerçekleşir ve hatalar hata listesinde hemen **gösterilir.**

* Canlı doğrulama, C# ve Visual Basic.

* Canlı bağımlılık doğrulamasını kullanırken tam çözüm analizini etkinleştirmek için Hata Listesinde görünen altın çubuktan seçenekler **ayarlarını açın.**

  - Çözümünüzde tüm mimari sorunları görmekle ilgilenmiyorsanız altın çıtayı kalıcı olarak çıkarabilirsiniz.
  - Tam çözüm analizini etkinleştirenin, analiz yalnızca düzende olan dosyalar için yapılır.

* Projeleri canlı doğrulamayı etkinleştirmek için yükseltirken dönüştürme işleminin ilerleme durumu bir iletişim kutusuyla görüntülenir.

* Bir projeyi canlı bağımlılık doğrulaması için güncelleştiriyorken, NuGet paketinin sürümü tüm projeler için aynı olacak şekilde yükseltilir ve kullanımda en yüksek sürümdür.

* Yeni bağımlılık doğrulama projesinin eklendiğinde proje güncelleştirmesi tetiklenir.

## <a name="see-if-an-item-supports-validation"></a>Bir öğenin doğrulamayı destekleyip desteklemediğini görme

Katmanları web sitelerine, Office belgelere, düz metin dosyalarına ve birden çok uygulama arasında paylaşılan proje dosyalarına bağabilirsiniz, ancak doğrulama işlemi bunları içermez. Doğrulama hataları, aralarında hiçbir bağımlılığın görünmediği ayrı katmanlara bağlanmış projelere veya derlemelere olan başvurular için görünmez. Kod bu başvuruları kullanmazsa böyle başvurular bağımlılık olarak düşünülmez.

1. Bağımlılık diyagramında, bir veya daha fazla katman seçin, seçiminize sağ tıklayın ve ardından Bağlantıları **Görüntüle'ye tıklayın.**

2. Katman **Gezgini'nde** Doğrulamayı Destekler **sütununa** bakın. Değer false ise, öğe doğrulamayı desteklemez.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Diğer .NET derlemelerini ve projelerini doğrulama için dahil etme

Öğeleri bağımlılık diyagramına sürüklerken, ilgili .NET derlemelerine veya projelerine yapılan  başvurular modelleme projesinde Katman Başvuruları klasörüne otomatik olarak eklenir. Bu klasör, doğrulama sırasında analiz edilen derlemeler ve projeler için başvurular içerir. Diğer .NET derlemelerini ve projelerini bağımlılık diyagramına el ile sürüklemeden doğrulama için ekleyebilirsiniz.

1. Bu **Çözüm Gezgini,** modelleme projesine veya Katman Başvuruları **klasörüne sağ** tıklayın ve ardından Başvuru Ekle'ye **tıklayın.**

2. Başvuru **Ekle iletişim kutusunda** derlemeleri veya projeleri seçin ve ardından Tamam'a **tıklayın.**

## <a name="validate-code-manually"></a>Kodu el ile doğrulama

Çözüm öğelerine bağlı açık bir bağımlılık diyagramınız varsa diyagramdan Kısayolu **doğrula** komutunu çalıştırabilirsiniz. **/p:ValidateArchitecture** özel özelliği True olarak ayarlanmış **şekilde msbuild** komutunu çalıştırmak için komut istemini de **kullanabilirsiniz.** Örneğin, kodda değişiklik yaparken bağımlılık çakışmalarını önceden yakalayabilmek için düzenli olarak katman doğrulama gerçekleştirin.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Açık bağımlılık diyagramından kodu doğrulama

1. Diyagram yüzeyine sağ tıklayın ve ardından Mimariyi **Doğrula'ya tıklayın.**

    > [!NOTE]
    > Bağımlılık diyagramı  (.layerdiagram) dosyasındaki Derleme Eylemi özelliği varsayılan olarak **Doğrula** olarak ayarlanır, böylece diyagram doğrulama sürecine dahil edilir.

     Hata **Listesi penceresi,** oluşan hataları raporlar. Doğrulama hataları hakkında daha fazla bilgi için [bkz. Katman doğrulama sorunlarını giderme.](#troubleshoot-layer-validation-issues)

2. Her hatanın kaynağını görüntülemek için Hata Listesi penceresinde **hataya çift** tıklayın.

    > [!NOTE]
    > Visual Studio kaynağı yerine bir kod eşlemesi gösterebilir. Bu durum, kodun bağımlılık diyagramı tarafından belirtilmemiş bir derlemeye bağımlılığı olduğunda veya kodda bağımlılık diyagramı tarafından belirtilen bir bağımlılık eksik olduğunda oluşur. Bağımlılığın mevcut olup olmadığını belirlemek için kod haritasını veya kodu gözden geçirme. Kod eşlemeleri hakkında daha fazla bilgi için [bkz. Çözümleriniz genelinde bağımlılıkları eşleme.](../modeling/map-dependencies-across-your-solutions.md)

3. Hataları yönetmek için [bkz. Katman doğrulama hatalarını çözümleme.](#resolve-layer-validation-errors)

### <a name="validate-code-at-the-command-prompt"></a>Komut isteminde kodu doğrulama

1. Visual Studio istemini açın.

2. Aşağıdakilerden birini seçin:

   - Kodu çözümde belirli bir modelleme projesine göre doğrulamak için MSBuild özel özelliğiyle çalıştırın.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - veya -

       Modelleme projesi (.modelproj) dosyasını ve bağımlılık diyagramını içeren klasöre göz atarak aşağıdaki özel MSBuild dosyasını çalıştırın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Çözümün tüm modelleme projelerinde kodu doğrulamak için MSBuild özel özelliğiyle çalıştırın:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - veya -

       Bağımlılık diyagramı içeren bir modelleme projesi içermesi gereken çözüm klasörüne gidin ve ardından aşağıdaki özel MSBuild ile aşağıdaki adımları çalıştırın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Oluşan hatalar listelenecektir. Görev hakkında daha fazla MSBuild için [bkz. MSBuild](../msbuild/msbuild.md) ve [MSBuild Görev.](../msbuild/msbuild-task.md)

   Doğrulama hataları hakkında daha fazla bilgi için [bkz. Katman doğrulama sorunlarını giderme.](#troubleshoot-layer-validation-issues)

### <a name="manage-validation-errors"></a>Doğrulama hatalarını yönetme

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdıysanız, Team Foundation'da bir iş öğesini günlüğe kayıt etmek iyi bir uygulamadır.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bu öğeye bağlantı oluşturmak için TFS Kaynak Kodu Denetimi'ne (SCC) zaten bağlı olduğunuzdan emin olun. Farklı bir TFS SCC'ye bağlantı açmaya çalışırsanız Visual Studio çözümü otomatik olarak kapatır. Bir iş öğesini oluşturmadan veya bağlamaya çalışmadan önce uygun SCC'ye zaten bağlı olduğunuzdan emin olun. Visual Studio'nin sonraki yayınlarında, bir SCC'ye bağlı değilken menü komutları kullanılamaz.

#### <a name="create-a-work-item-for-a-validation-error"></a>Doğrulama hatası için iş öğesi oluşturma

- Hata **Listesi penceresinde** hataya sağ tıklayın, İş Öğesi Oluştur'a **gelin** ve ardından oluşturmak istediğiniz iş öğesinin türüne tıklayın.

Hata Listesi penceresinde doğrulama hatalarını yönetmek için **şu görevleri** kullanın:

|**Kime**|**Buradaki adımları izleyin**|
|-|-|
|Doğrulama sırasında seçili hataları gizleme|Seçili bir veya birden çok hataya sağ tıklayın, Doğrulama Hatalarını **Yönet'in** üzerine gelin ve Ardından Hataları **Bastır'a tıklayın.**<br /><br /> Gizlenen hatalar üstü çizili biçimde görünür. Doğrulamayı daha sonra çalıştırdığınızda bu hatalar görünmez.<br /><br /> Gizlenen hatalar, ilgili bağımlılık diyagramı dosyası için bir .suppressions dosyasında izılır.|
|Seçili hataların gizlenmesini durdurma|Seçili gizlenen hataya veya hatalara sağ tıklayın, Doğrulama Hatalarını Yönet'in üzerine **gelin** ve Ardından Hataları **Gizlemeyi Durdur'a tıklayın.**<br /><br /> Doğrulamayı daha sonra çalıştırdığınızda seçili gizlenen hatalar görünecektir.|
|Hata Listesi penceresinde gizlenen tüm **hataları geri** yükleme|Hata Listesi penceresinde herhangi bir yere **sağ tıklayın,** Doğrulama Hatalarını Yönet'in üzerine **gelin** ve ardından Tüm Gizlenen Hataları Göster **'e tıklayın.**|
|Tüm gizlenen hataları Hata Listesi **penceresinden** gizle|Hata Listesi penceresinde herhangi bir yere **sağ tıklayın,** Doğrulama Hatalarını Yönet'in üzerine **gelin** ve ardından Gizlenen Tüm Hataları **Gizle 'ye tıklayın.**|

## <a name="validate-code-automatically"></a>Kodu otomatik olarak doğrulama

Her yerel bir yapı çalıştırışınızda katman doğrulama gerçekleştirebilirsiniz. Takımınız Azure DevOps kullanıyorsa, özel bir MSBuild görevi oluşturarak belirtebilirsiniz ve doğrulama hatalarını toplamak için derleme raporlarını kullanarak geçitli iadelerle katman doğrulaması gerçekleştirebilirsiniz. Geçitli iade derlemeleri oluşturmak için bkz. [TFVC geçitli iade.](/azure/devops/pipelines/build/triggers)

### <a name="to-validate-code-automatically-during-a-local-build"></a>Kodu yerel yapı sırasında otomatik olarak doğrulamak için

Modelleme projesi (.modelproj) dosyası açmak için metin düzenleyicisi kullanın ve ardından aşağıdaki özelliği ekleyin:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- veya

1. **Çözüm Gezgini**' de, bağımlılık diyagramı veya diyagramlarını içeren modelleme projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellikler** penceresinde, modelleme projesinin **Mimariyi Doğrula** özelliğini **doğru** olarak ayarlayın.

    Bu, doğrulama işlemi içinde modelleme projesini içerir.

3. **Çözüm Gezgini**, doğrulama için kullanmak istediğiniz bağımlılık diyagramı (. layerdiagram) dosyasına tıklayın.

4. **Özellikler** penceresinde diyagramın **Build Action** özelliğinin **Validate** olarak ayarlandığından emin olun.

    Bu, doğrulama işlemindeki bağımlılık diyagramını içerir.

Hata Listesi penceresindeki hataları yönetmek için bkz. [katman doğrulama hatalarını çözümleme](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Katman doğrulama sorunlarını giderme

Aşağıdaki tabloda katman doğrulama sorunları ve bunların çözümü açıklanmaktadır. Bu sorunlar, kod ve tasarım arasındaki çakışmalarla sonuçlanan hatalardan ayrılır. Bu hatalar hakkında daha fazla bilgi için bkz. [katman doğrulama sorunlarını giderme](#troubleshoot-layer-validation-issues).

|**Sorun**|**Olası neden**|**Çözünürlük**|
|-|-|-|
|Doğrulama hataları beklendiği gibi gerçekleşmez.|Doğrulama, Çözüm Gezgini ' deki diğer bağımlılık diyagramlarından kopyalanmış ve aynı modelleme projesinde olan bağımlılık diyagramlarında çalışmaz. Bu şekilde kopyalanmış bağımlılık diyagramları, özgün bağımlılık diyagramı ile aynı başvuruları içerir.|Modelleme projesine yeni bir bağımlılık diyagramı ekleyin.<br /><br /> Öğeleri kaynak bağımlılığı diyagramından yeni diyagrama kopyalayın.|

## <a name="resolve-layer-validation-errors"></a>Katman doğrulama hatalarını çözümleme

Kodu bir bağımlılık diyagramına karşı doğruladığınızda, kod tasarımla çakışıyorsa doğrulama hataları oluşur. Örneğin, aşağıdaki durumlar doğrulama hatalarının oluşmasına neden olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu görevi yinelemeli bir şekilde gerçekleştirebilirsiniz.

Aşağıdaki bölümde, bu hatalarda kullanılan sözdizimi belirtilmekte, bu hataların anlamı açıklanmakta ve bunları çözmek veya yönetmek için yapabilecekleriniz önerilmektedir.

|**Syntax**|**Açıklama**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* , bağımlılık diyagramındaki bir katmanla ilişkili bir yapıdır.<br /><br /> *ArtifactTypeN* , bir **sınıf** veya **Yöntem** gibi *ArtifactN* türüdür, örneğin:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Bir ad alanının adı.|
|*Layernamence*|Bağımlılık diyagramındaki bir katmanın adı.|
|*DependencyType*|*Artifact1* ve *Artifact2* arasındaki bağımlılık ilişkisinin türü. Örneğin, *Artifact1* , *Artifact2* ile bir **çağrı** ilişkisine sahiptir.|

| **Hata sözdizimi** | **Hata açıklaması** |
|-|-|
| DV0001: **geçersiz bağımlılık** | Bu sorun, bir katmana eşlenen bir kod öğesi (ad alanı, tür, üye) başka bir katmana eşlenmiş bir kod öğesine başvuruyorsa, ancak bu katmanları içeren bağımlılık doğrulama diyagramında bu katmanlar arasında bağımlılık oku olmadığında raporlanır. Bu bir bağımlılık kısıtlaması ihlalidir. |
| DV1001: **geçersiz ad alanı adı** | Bu sorun, "Izin verilen ad alanı adları" özelliği bu kod öğesinin tanımlandığı ad alanını içermediği bir katmanla ilişkili bir kod öğesinde raporlanır. Bu bir adlandırma kısıtlaması ihlalidir. "Izin verilen ad alanı adları" sözdiziminin, katman olarak ilişkilendirilmiş kod öğelerinin tanımlanmasına izin verilen ad alanlarının noktalı virgülle bir listesi olacağını unutmayın. |
| DV1002: **Referenceable ad alanına bağımlılık** | Bu sorun, katman ile ilişkili bir kod öğesinde raporlanır ve katmanın "Referenceable namespace" özelliğinde tanımlanan bir ad alanında tanımlanan başka bir kod öğesine başvuracaktır. Bu bir adlandırma kısıtlaması ihlalidir. "Başvurulmayan ad alanları" özelliğinin, bu katmanla ilişkili kod öğelerinde başvurulmaması gereken, noktalı virgülle ayrılmış ad alanları listesi olarak tanımlandığını unutmayın. |
| DV1003: **Izin verilmeyen ad alanı adı** | Bu sorun, "Izin verilmeyen ad alanı adları" özelliği bu kod öğesinin tanımlandığı ad alanını içerdiği bir katmanla ilişkili bir kod öğesinde raporlanır. Bu bir adlandırma kısıtlaması ihlalidir. "Izin verilmeyen ad alanı adı" özelliğinin, bu katman ile ilişkili kod öğelerinin tanımlanmadığı ad alanlarının noktalı virgülle ayrılmış bir listesi olarak tanımlandığını unutmayın. |
| DV2001: **Katman diyagramı varlık** | Bu sorun, bağımlılık diyagramı dosyası içermeyen bir projede raporlanır, ancak bağımlılık doğrulama Çözümleyicileri anlamına gelir. Bağımlılık doğrulaması kullanılmıyorsa, "Microsoft. DependencyValidation. çözümleyiciler" öğesini doğrudan Çözüm Gezgini kaldırabilir veya bu uyarıyı gizleyebilirsiniz. Bir bağımlılık diyagramı eklemek için bkz. [kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md). |
| DV2002: **eşlenmemiş türler tabanı** | Bu sorun, bir kod öğesi herhangi bir katmana eşlenmezse raporlanır. |
| DV3001: **eksik bağlantı** | '*LayerName*' katmanı, bulunamayan '*yapıt*' öğesine bağlanır. Eksik bir derleme başvurunuz mu var? |
| DV9001: **mimari analizi iç hatalar buldu** | Sonuçlar tamamlanmamış olabilir. Daha fazla bilgi için ayrıntılı yapı olay günlüğü veya çıkış penceresine bakın. |

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da canlı bağımlılık doğrulaması](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
- [Video: mimari bağımlılıklarınızı gerçek zamanlı olarak doğrulama](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
