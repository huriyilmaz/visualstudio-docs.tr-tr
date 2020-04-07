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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759706"
---
# <a name="validate-code-with-dependency-diagrams"></a>Bağımlılık diyagramları ile kod doğrulama

## <a name="why-use-dependency-diagrams"></a>Bağımlılık diyagramlarını neden kullanıyorsun?

Kodun tasarımıyla çakışmadığından emin olmak için, Visual Studio'da bağımlılık diyagramlarıyla kodunuzu doğrulayın. Bu, şu konularda size yardımcı olabilir:

- Kodunuzdaki bağımlılıklar ile bağımlılık diyagramındaki bağımlılıklar arasındaki çakışmaları bulun.

- Önerilen değişiklikler tarafından etkilenebilecek bağımlılıkları bulun.

   Örneğin, bağımlılık diyagramını olası mimari değişiklikleri göstermek için ve etkilenen bağımlılıkları görmek için kodu doğrulayabilirsiniz.

- Kodu yeniden düzenleyin veya kodu farklı bir tasarıma geçirin.

   Kodu farklı bir mimariye taşıdığınız zaman iş gerektiren kodu veya bağımlılıkları bulun.

**Gereksinimler**

- Visual Studio

  Bir .NET Core projesi için bağımlılık diyagramı oluşturmak için Visual Studio 2019 sürüm 16.2 veya sonraki sürümolmalıdır.

- Bağımlılık diyagramı olan bir modelleme projesi olan bir çözüm. Bu bağımlılık diyagramı, doğrulamak istediğiniz C# veya Visual Basic projelerindeki yapılara bağlanmalıdır. Bkz. [Kodunuzdan bağımlılık diyagramları oluştur.](../modeling/create-layer-diagrams-from-your-code.md)

Visual Studio'nun hangi sürümlerinin bu özelliği desteklediğini görmek [için mimari ve modelleme araçları için Edition desteğine](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)bakın.

Visual Studio'daki açık bağımlılık diyagramından veya komut isteminden kodu el ile doğrulayabilirsiniz. Yerel yapılar veya Azure Ardışık Hatları oluşturur çalışırken kodu otomatik olarak doğrulayabilirsiniz. [Bkz. Kanal 9 Videosu: Bağımlılık diyagramlarını kullanarak mimarinizi tasarlayın ve doğrulayın.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

> [!IMPORTANT]
> Team Foundation Server (TFS) kullanarak katman doğrulamayı çalıştırmak istiyorsanız, Visual Studio'nun aynı sürümünü yapı sunucunuza da yüklemeniz gerekir.

## <a name="live-dependency-validation"></a>Canlı bağımlılık doğrulaması

Bağımlılık doğrulama gerçek zamanlı olarak gerçekleşir ve hatalar **hata listesinde**hemen gösterilir.

* Canlı doğrulama C# ve Visual Basic için desteklenir.

* Canlı bağımlılık doğrulaması kullanırken tam çözüm çözümlemesini etkinleştirmek **için, Hata Listesinde**görünen altın çubuğundan seçenek ayarlarını açın.

  - Eğer çözüm tüm mimari sorunları görmek le ilgilenmiyorsanız kalıcı olarak altın çubuğu kapatabilirsiniz.
  - Tam çözüm çözümlemesini etkinleştiremezseniz, çözümleme yalnızca düzenlenen dosyalar için yapılır.

* Canlı doğrulamayı etkinleştirmek için projeleri yükseltirken, bir iletişim kutusu dönüştürmenin ilerlemesini gösterir.

* Canlı bağımlılık doğrulaması için bir proje güncellenirken, NuGet paketinin sürümü tüm projeler için aynı olacak şekilde yükseltilir ve kullanılan en yüksek sürümdür.

* Yeni bir bağımlılık doğrulama projesi eklemek bir proje güncelleştirmesi tetikler.

## <a name="see-if-an-item-supports-validation"></a>Bir öğenin doğrulamayı destekleyip desteklemediğini görme

Katmanları web sitelerine, Office belgelerine, düz metin dosyalarına ve birden çok uygulamada paylaşılan projelerdeki dosyalara bağlayabilirsiniz, ancak doğrulama işlemi bunları içermez. Doğrulama hataları, aralarında hiçbir bağımlılığın görünmediği ayrı katmanlara bağlanmış projelere veya derlemelere olan başvurular için görünmez. Kod bu başvuruları kullanmazsa böyle başvurular bağımlılık olarak düşünülmez.

1. Bağımlılık diyagramında, bir veya daha fazla katman seçin, seçiminizi sağ tıklatın ve ardından **Bağlantıları Görüntüle'yi**tıklatın.

2. **Katman Gezgini'nde,** **Destekdoğrulama** sütununa bakın. Değer false ise, öğe doğrulamayı desteklemez.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Diğer .NET derlemelerini ve projelerini doğrulama için dahil etme

Öğeleri bağımlılık diyagramına sürüklediğinizde, ilgili .NET derlemelerine veya projelere yapılan başvurular modelleme projesindeki **Katman Başvuruları** klasörüne otomatik olarak eklenir. Bu klasör, doğrulama sırasında analiz edilen derlemeler ve projeler için başvurular içerir. Diğer .NET derlemelerini ve projeleri, bağımlılık diyagramına el ile sürüklemeden doğrulama için ekleyebilirsiniz.

1. **Çözüm Gezgini'nde,** modelleme projesini veya **Katman Başvuruları** klasörünü sağ tıklatın ve ardından Başvuru **Ekle'yi**tıklatın.

2. Başvuru **Ekle** iletişim kutusunda derlemeleri veya projeleri seçin ve ardından **Tamam'ı**tıklatın.

## <a name="validate-code-manually"></a>Kodu el ile doğrulama

Çözüm öğelerine bağlı açık bir bağımlılık diyagramınvarsa, diyagramdan **doğrulama** kısayol komutunu çalıştırabilirsiniz. **Msbuild** komutunu **/p:ValidateArchitecture** özel özellik kümesi True ile çalıştırmak **True**için komut istemini de kullanabilirsiniz. Örneğin, kodda değişiklik yaparken bağımlılık çakışmalarını önceden yakalayabilmek için düzenli olarak katman doğrulama gerçekleştirin.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Kodu açık bağımlılık diyagramından doğrulama

1. Diyagram yüzeyine sağ tıklayın ve ardından **Mimari'yi Doğrula'yı**tıklatın.

    > [!NOTE]
    > Varsayılan olarak, bağımlılık diyagramı (.layerdiagram) dosyasındaki **Eylem Oluştur** özelliği, diyagramın doğrulama işlemine dahil edilebis olması için **Doğrula'ya** ayarlanır.

     **Hata Listesi** penceresi, oluşan hataları bildirir. Doğrulama hataları hakkında daha fazla bilgi için [Sorun Giderme katmanı doğrulama sorunlarına](#troubleshoot-layer-validation-issues)bakın.

2. Her hatanın kaynağını görüntülemek için **Hata Listesi** penceresindeki hatayı çift tıklatın.

    > [!NOTE]
    > Visual Studio hatanın kaynağı yerine bir kod eşlemi gösterebilir. Bu, kodun bağımlılık diyagramı tarafından belirtilmeyen bir derlemeye bağımlılığı olduğunda veya kod bağımlılık diyagramı tarafından belirtilen bir bağımlılık eksikolduğunda oluşur. Bağımlılığın var olup olmadığını belirlemek için kod eşlemi veya kodu gözden geçirin. Kod eşlemleri hakkında daha fazla bilgi için [çözümlerinizdeki Harita bağımlılıklarına](../modeling/map-dependencies-across-your-solutions.md)bakın.

3. Hataları yönetmek için katman [doğrulama hatalarını](#resolve-layer-validation-errors)çözümle'ye bakın.

### <a name="validate-code-at-the-command-prompt"></a>Komut isteminde kodu doğrula

1. Visual Studio komut istemini açın.

2. Aşağıdakilerden birini seçin:

   - Çözümdeki belirli bir modelleme projesine karşı kodu doğrulamak için MSBuild'i aşağıdaki özel özellik ile çalıştırın.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - veya -

       Modelleme projesi (.modelproj) dosyasını ve bağımlılık diyagramını içeren klasöre göz atın ve ardından MSBuild'i aşağıdaki özel özellik ile çalıştırın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Çözümdeki tüm modelleme projelerine karşı kodu doğrulamak için MSBuild'i aşağıdaki özel özellik ile çalıştırın:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - veya -

       Bağımlılık diyagramı içeren bir modelleme projesi içermesi gereken çözüm klasörüne göz atın ve ardından MSBuild'i aşağıdaki özel özellik ile çalıştırın:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Oluşan hatalar listelenecektir. MSBuild hakkında daha fazla bilgi için [MSBuild](../msbuild/msbuild.md) ve [MSBuild Görev'e](../msbuild/msbuild-task.md)bakın.

   Doğrulama hataları hakkında daha fazla bilgi için [Sorun Giderme katmanı doğrulama sorunlarına](#troubleshoot-layer-validation-issues)bakın.

### <a name="manage-validation-errors"></a>Doğrulama hatalarını yönetme

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdığınızda, bir iş öğesini Team Foundation'da günlüğe kaydetmek iyi bir uygulamadır.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bağlantı kurmak için TFS Kaynak Kodu Denetimi'ne (SCC) zaten bağlı olmalısınız. Farklı bir TFS SCC bağlantısı açmaya çalışırsanız, Visual Studio geçerli çözümü otomatik olarak kapatır. Bir iş öğesi oluşturmaya veya bağlantı kurmaya çalışmadan önce uygun SCC'ye zaten bağlı olduğunuzu sağlayın. Visual Studio'nun sonraki sürümlerinde, bir SCC'ye bağlı değilseniz menü komutları kullanılamaz.

#### <a name="create-a-work-item-for-a-validation-error"></a>Doğrulama hatası için çalışma öğesi oluşturma

- Hata **Listesi** penceresinde, hatayı sağ tıklatın, **İş Öğesi Oluştur'a**işaret edin ve ardından oluşturmak istediğiniz iş öğesi türünü tıklatın.

**Hata Listesi** penceresinde doğrulama hatalarını yönetmek için bu görevleri kullanın:

|**Hedef**|**Aşağıdaki adımları izleyin**|
|-|-|
|Doğrulama sırasında seçili hataları gizleme|Bir veya birden çok seçili hatayı sağ tıklatın, **Doğrulama Hatalarını Yönetme'yi**işaret edin ve ardından **Hataları Bastır'ı**tıklatın.<br /><br /> Gizlenen hatalar üstü çizili biçimde görünür. Doğrulamayı daha sonra çalıştırdığınızda bu hatalar görünmez.<br /><br /> Bastırılan hatalar, ilgili bağımlılık diyagramı dosyası için bir .suppressions dosyasında izlenir.|
|Seçili hataların gizlenmesini durdurma|Seçili bastırılmış hata veya hataları sağ tıklatın, **Doğrulama Hatalarını Yönetme'yi**işaret edin ve ardından **Hataları Bastırmayı Durdur'u**tıklatın.<br /><br /> Doğrulamayı daha sonra çalıştırdığınızda seçili gizlenen hatalar görünecektir.|
|**Hata Listesi** penceresindeki tüm bastırılan hataları geri yükleme|**Hata Listesi** penceresinde herhangi bir yere sağ tıklayın, **Doğrulama Hatalarını Yönetme'yi**işaret edin ve ardından Tüm **Bastırılan Hataları Göster'i**tıklatın.|
|**Hata Listesi** penceresinden bastırılan tüm hataları gizleme|**Hata Listesi** penceresinde herhangi bir yere sağ tıklayın, **Doğrulama Hatalarını Yönetme'yi**işaret edin ve ardından Tüm **Bastırılan Hataları Gizle'yi**tıklatın.|

## <a name="validate-code-automatically"></a>Kodu otomatik olarak doğrulama

Her yerel bir yapı çalıştırışınızda katman doğrulama gerçekleştirebilirsiniz. Ekibiniz Azure DevOps kullanıyorsa, özel bir MSBuild görevi oluşturarak belirtebileceğiniz ve doğrulama hatalarını toplamak için yapı raporlarını kullanabileceğiniz kapılı iadelerle katman doğrulaması gerçekleştirebilirsiniz. Geçitli iade yapılarını oluşturmak için [TFVC kapılı iade](/azure/devops/pipelines/build/triggers)ye bakın.

### <a name="to-validate-code-automatically-during-a-local-build"></a>Kodu yerel yapı sırasında otomatik olarak doğrulamak için

Modelleme projesi (.modelproj) dosyası açmak için metin düzenleyicisi kullanın ve ardından aşağıdaki özelliği ekleyin:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\-veya -

1. **Çözüm Gezgini'nde,** bağımlılık diyagramı veya diyagramları içeren modelleme projesini sağ tıklatın ve ardından **Özellikler'i**tıklatın.

2. **Özellikler** penceresinde, modelleme projesinin Mimari **özelliğini** **True**olarak ayarlayın.

    Bu, doğrulama işlemi içinde modelleme projesini içerir.

3. **Çözüm Gezgini'nde,** doğrulama için kullanmak istediğiniz bağımlılık diyagramı (.layerdiagram) dosyasını tıklatın.

4. **Özellikler** penceresinde, diyagramın **Yapı Eylemi** özelliğinin **doğrulamak**üzere ayarlandıklarından emin olun.

    Bu doğrulama işleminde bağımlılık diyagramı içerir.

Hata Listesi penceresindeki hataları yönetmek için [bkz.](#resolve-layer-validation-errors)

## <a name="troubleshoot-layer-validation-issues"></a>Katman doğrulama sorunlarını giderme

Aşağıdaki tabloda katman doğrulama sorunları ve bunların çözümü açıklanmaktadır. Bu sorunlar, kod ve tasarım arasındaki çakışmalarla sonuçlanan hatalardan ayrılır. Bu hatalar hakkında daha fazla bilgi için [Sorun Giderme katmanı doğrulama sorunlarına](#troubleshoot-layer-validation-issues)bakın.

|**Sorunu**|**Olası Neden**|**Çözünürlük**|
|-|-|-|
|Doğrulama hataları beklendiği gibi gerçekleşmez.|Doğrulama, Çözüm Gezgini'ndeki diğer bağımlılık diyagramlarından kopyalanan ve aynı modelleme projesinde olan bağımlılık diyagramlarında çalışmaz. bu şekilde kopyalanan bağımlılık diyagramları, özgün bağımlılık diyagramıyla aynı başvuruları içerir.|Modelleme projesine yeni bir bağımlılık diyagramı ekleyin.<br /><br /> Kaynakları bağımlılık diyagramından yeni diyagrama kopyalayın.|

## <a name="resolve-layer-validation-errors"></a>Katman doğrulama hatalarını çözümle

Bir bağımlılık diyagramına karşı kodu doğruladiğinizde, kod tasarımla çakıştığında doğrulama hataları oluşur. Örneğin, aşağıdaki durumlar doğrulama hatalarının oluşmasına neden olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu görevi yinelemeli bir şekilde gerçekleştirebilirsiniz.

Aşağıdaki bölümde, bu hatalarda kullanılan sözdizimi belirtilmekte, bu hataların anlamı açıklanmakta ve bunları çözmek veya yönetmek için yapabilecekleriniz önerilmektedir.

|**Sözdizimi**|**Açıklama**|
|-|-|
|*Artifon*(*ArtifactTypeN*)|*Arteiş,* bağımlılık diyagramındaki bir katmanla ilişkili bir yapıdır.<br /><br /> *ArtifactTypeN,* **Sınıf** veya **Yöntem**gibi *Arteiş*Türüdür, örneğin:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Bir ad alanının adı.|
|*LayerNameN*|Bağımlılık diyagramındaki bir katmanın adı.|
|*Dependencytype*|*Artefakt1* ve *Artifakı2*arasındaki bağımlılık ilişkisitürü. Örneğin, *Artefakt1'in* *Artefakt2*ile **Bir Çağrı** ilişkisi vardır.|

| **Hata Sözdizimi** | **Hata Açıklaması** |
|-|-|
| DV0001: **Geçersiz Bağımlılık** | Bu sorun, katmana eşlenen bir kod öğesi başka bir katmana eşlendiğinde bir kod öğesi eşlendiğinde, bu katmanları içeren bağımlılık doğrulama diyagramında bu katmanlar arasında bağımlılık oku bulunmadığında bu sorun bildirilir. Bu bir bağımlılık kısıtlaması ihlalidir. |
| DV1001: **Geçersiz ad alanı adı** | Bu sorun, "İzin Verilen Ad Alanı Adları" özelliğinin bu kod öğesinin tanımlandığı ad alanını içermediği bir katmanla ilişkili bir kod öğesi üzerinde bildirilir. Bu bir adlandırma kısıtlaması ihlalidir. "İzin Verilen Ad Alanı Adları" sözdiziminin, ilişkili kod öğelerinin tanımlanmasına izin verilen ad alanlarının yarı sütunlu bir listesi olacağını unutmayın. |
| DV1002: **Başvurulan ad alanına bağımlılık** | Bu sorun, katmanla ilişkili bir kod öğesi üzerinde raporlanır ve katmanın "Başvurulan Ad Alanı" özelliğinde tanımlanan bir ad alanında tanımlanan başka bir kod öğesine başvurur. Bu bir adlandırma kısıtlaması ihlalidir. "Başvurulan Ad Alanları" özelliğinin, bu katmanla ilişkili kod öğelerine başvurulmaması gereken ad alanlarının yarı nokta ayrı bir listesi olarak tanımlandığını unutmayın. |
| DV1003: **İzin verilmeyen ad alanı adı** | Bu sorun, "İzin Verilmeyen Ad Alanı Adları" özelliğinin bu kod öğesinin tanımlandığı ad alanını içerdiği bir katmanla ilişkili bir kod öğesi üzerinde bildirilir. Bu bir adlandırma kısıtlaması ihlalidir. "İzin verilmeyen ad alanı adı" özelliğinin, bu Katmanla ilişkili kod öğelerinin tanımlanmaması gereken yarı nokta ayrı ad alanları listesi olarak tanımlandığını unutmayın. |
| DV2001: **Katman Diyagramı Varlığı** | Bu sorun, bağımlılık diyagramı dosyası içermeyen, ancak bağımlılık doğrulaması çözümleyicileri anlamına gelen bir projede bildirilir. Bağımlılık Doğrulama sı kullanılmamışsa, "Microsoft.DependencyValidation.Analyzers" adresini doğrudan Solution Explorer'dan kaldırabilir veya bu uyarıyı bastırabilirsiniz. Bağımlılık diyagramı eklemek için [bkz.](../modeling/create-layer-diagrams-from-your-code.md) |
| DV2002: **Eşlenmemiş Tipler Tabanı** | Bu sorun, bir kod öğesi herhangi bir katmana eşlenmediğinde bildirilir. |
| DV3001: **Eksik Bağlantı** | Katman '*LayerName*' bağlantıları '*Artifakı*' bulunamaz. Eksik bir derleme başvurunuz mu var? |
| DV9001: **Mimari analiz iç hatalar bulundu** | Sonuçlar tamamlanmamış olabilir. Daha fazla bilgi için ayrıntılı yapı olay günlüğü veya çıkış penceresine bakın. |

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da canlı bağımlılık doğrulama](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
- [Video: Mimari bağımlılıklarınızı gerçek zamanlı olarak doğrulayın](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
