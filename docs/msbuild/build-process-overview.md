---
title: MSBuild nasıl proje oluşturur
description: İster MSBuild ister komut satırı ya da betikten Visual Studio proje dosyalarınızı nasıl işleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ad648b114ffd067ef1ab5d9a0ea1671d03207396
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077718"
---
# <a name="how-msbuild-builds-projects"></a>MSBuild nasıl proje oluşturur

Bu MSBuild nasıl çalışır? Bu makalede, ister MSBuild ister komut Visual Studio betikten çağrılan proje dosyalarınızı nasıl işleyebilirsiniz? Bu MSBuild bilmek sorunları daha iyi tanılamanıza ve derleme sürecinizi daha iyi özelleştirmenize yardımcı olabilir. Bu makalede derleme işlemi açıklanmıştır ve büyük ölçüde tüm proje türleri için geçerlidir.

Tam derleme işlemi, projeyi [derlemek için ilk başlatma,](#startup) [değerlendirme](#execution-phase) ve hedef ve görevlerin yürütülmesini içerir. [](#evaluation-phase) Bu girişlere ek olarak, dış içeri aktarmalar hem *Microsoft.Common.targets* gibi standart içeri [](#user-configurable-imports) aktarmalar hem de çözüm veya proje düzeyinde kullanıcı tarafından yapılandırılabilir içeri aktarmalar da dahil olmak üzere derleme işleminin ayrıntılarını tanımlar. [](#standard-imports)

## <a name="startup"></a>Başlangıç

MSBuild Visual StudioMicrosoft.Build.dll'daki *MSBuild* nesne modeli aracılığıyla ya da yürütülebilir dosya doğrudan komut satırı veya CI sistemlerinde olduğu gibi bir betikte çağrılarak çağrılabilir. Her iki durumda da, derleme işlemini etkileyen girişler proje dosyasını (veya Visual Studio'a iç proje nesnesini), muhtemelen bir çözüm dosyasını, ortam değişkenlerini ve komut satırı anahtarlarını ya da nesne modeli eşdeğerlerini içerir. Başlatma aşamasında, günlükçileri yapılandırma gibi farklı ayarları yapılandırmak MSBuild komut satırı seçenekleri veya nesne modeli eşdeğerleri kullanılır. veya anahtarı kullanılarak komut satırına ayarlanmış özellikler genel özellikler olarak ayarlanır. Bu özellik, proje dosyaları daha sonra okunsa bile proje dosyalarında ayarlanmayacak `-property` `-p` değerleri geçersiz kılar.

Sonraki bölümler çözüm dosyaları veya proje dosyaları gibi giriş dosyalarıyla ilgilidir.

### <a name="solutions-and-projects"></a>Çözümler ve projeler

MSBuild örnekleri bir çözümün parçası olarak bir veya birden çok projeden oluşur. Çözüm dosyası bir MSBuild XML dosyası değildir ancak MSBuild, verilen yapılandırma ve platform ayarları için gerekli tüm projeleri bilmek için yorumlanır. Bu MSBuild xml girişini işleyene kadar çözüm derlemesi olarak adlandırılır. Her çözüm derlemesinde bir şey çalıştırmaya olanak sağlayan bazı genişletilebilir noktaları vardır, ancak bu derleme tek tek proje derlemelerinden ayrı bir çalıştırma olduğu için, çözüm derlemesinde yer alan özellik veya hedef tanımların ayarları her proje derlemesi için uygun değildir.

Çözüm derlemeyi özelleştirme'de çözüm derlemenin nasıl [genişletebileceğinizi bulabilirsiniz.](customize-your-build.md#customize-the-solution-build)

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio derlemeler ve MSBuild.exe karşılaştırması

Projelerin Visual Studio'de derlemesi ile MSBuild yürütülebilir dosyası aracılığıyla MSBuild çağırmanız veya MSBuild derlemeyi başlatmak için MSBuild nesne modelini kullanma arasında bazı önemli farklar vardır. Visual Studio derlemeler için proje derleme Visual Studio yönetir; yalnızca MSBuild proje düzeyinde çağrı yapar ve çağıran bir dizi Boole özelliği ( , ) kümenin ne yaptığını önemli `BuildingInsideVisualStudio` `BuildProjectReferences` ölçüde etkileyen MSBuild ayarlanır. Her projenin içinde yürütme, MSBuild çağrıldığında olduğu gibi gerçekleşir, ancak başvurulan projelerde fark oluşur. Bu MSBuild, başvurulan projeler gerektiğinde aslında bir derleme gerçekleşir; diğer bir ifadeyle, görevleri ve araçları çalıştırır ve çıkışı oluşturur. Bir Visual Studio bir proje bulduğunda, MSBuild yalnızca başvurulan projeden beklenen çıkışları döndürür; bu Visual Studio diğer projelerin binalarını denetlemenizi sağlar. Visual Studio, derleme sırası belirler ve tamamen MSBuild denetimi altında ayrı olarak Visual Studio çağrılar.

Çözüm dosyasıyla MSBuild, çözüm MSBuild dosyasını ayrıştırır, standart bir XML giriş dosyası oluşturur, değerlendirir ve proje olarak yürütür. Çözüm derlemesi herhangi bir projeden önce yürütülür. Bu Visual Studio, bunların hiçbiri olmaz; MSBuild hiçbir zaman çözüm dosyasını görmez. Sonuç olarak, çözüm derleme özelleştirmesi (daha önce *kullanarak). SolutionName.sln.targets ve* *sonrası. SolutionName.sln.targets*) yalnızca MSBuild.exe veya nesne modeli odaklı için geçerlidir, Visual Studio geçerlidir.

### <a name="project-sdks"></a>Proje SDK’leri

Proje dosyalarının MSBuild SDK özelliği görece yenidir. Bu değişiklik öncesinde, proje dosyaları belirli bir proje türü için derleme işlemini tanımlanan *.targets* ve *.props* dosyalarını açıkça içe aktardı.

.NET Core projeleri, .NET SDK'nın onlara uygun sürümünü içeri aktarın. Genel bakış, [.NET Core proje SDK'ları](/dotnet/core/project-sdk/overview)ve özellikleri başvurusuna [bakın.](/dotnet/core/project-sdk/msbuild-props)

## <a name="evaluation-phase"></a>Değerlendirme aşaması

Bu bölümde, bu giriş dosyalarının nelerin üretileceklerini belirleyen bellek içinde nesneler üretmek için nasıl işlenmeleri ve ayrıştırıldıkları ele alın almaktadır.

Değerlendirme aşamasının amacı, giriş XML dosyalarına ve yerel ortama göre bellekte nesne yapıları oluşturmaktır. Değerlendirme aşaması, proje XML dosyaları gibi giriş dosyalarını ve genellikle *.props* veya *.targets* dosyaları olarak adlandırılmış, içe aktarılan XML dosyaları gibi giriş dosyalarını işlemeye yönelik altı geçişden oluşur. Bunlar öncelikli olarak özellikleri ayarlayarak veya derleme hedeflerini tanımlar. Her geçiş, daha sonra projeleri derlemek için yürütme aşamasında kullanılan bellek içinde nesnelerin bir bölümünü oluşturur, ancak değerlendirme aşamasında gerçek derleme eylemi oluşmaz. Her geçişte öğeler, görünme sırasına göre işlenir.

Değerlendirme aşamasındaki geçişler aşağıdaki gibidir:

- Ortam değişkenlerini değerlendirme
- İçeri aktarmaları ve özellikleri değerlendirme
- Öğe tanımlarını değerlendirme
- Öğeleri değerlendirme
- [UsingTask öğelerini](usingtask-element-msbuild.md) değerlendirme
- Hedefleri değerlendirme

Bu geçişlerin sırası önemli etkileri vardır ve proje dosyasını özelleştirerek bilmek önemlidir. Bkz. [Özellik ve öğe değerlendirme sırası.](comparing-properties-and-items.md#property-and-item-evaluation-order)

### <a name="evaluate-environment-variables"></a>Ortam değişkenlerini değerlendirme

Bu aşamada, ortam değişkenleri eşdeğer özellikleri ayarlamak için kullanılır. Örneğin, PATH ortam değişkeni özelliği olarak kullanılabilir `$(PATH)` yapılır. Komut satırı veya betikten çalıştır olduğunda, komut ortamı normal olarak kullanılır ve Visual Studio çalıştırıla Visual Studio ortam kullanılır.

### <a name="evaluate-imports-and-properties"></a>İçeri aktarmaları ve özellikleri değerlendirme

Bu aşamada, proje dosyaları ve içeri aktarma zincirinin tamamı dahil olmak üzere tüm giriş XML'i okunur. MSBuild projenin XML'ini ve tüm içe aktarılan dosyaları temsil eden bir bellek içinde XML yapısı oluşturur. Şu anda hedeflerde olmayan özellikler değerlendirilir ve ayarlanır.

Tüm XML MSBuild okuma işleminin bir sonucu olarak, derleme işlemi sırasında bu girişlerde yapılan değişiklikler geçerli derlemeyi etkilemez.

Herhangi bir hedefin dışındaki özellikler, hedeflerin içindeki özelliklerden farklı şekilde ele alınan özelliklerdir. Bu aşamada, yalnızca herhangi bir hedefin dışında tanımlanan özellikler değerlendirilir.

Özellikler, geçişte sırayla işlendiğinden, girişteki herhangi bir noktadaki bir özellik, girişte daha önce görünen ancak daha sonra görünen özelliklere erişemeyecek olan özellik değerlerine erişebilirsiniz.

Özellikler öğeler değerlendirilmeden önce işlendiğinden, özelliklerin herhangi bir bölümü geçiş sırasında herhangi bir öğenin değerine erişesiniz. 

### <a name="evaluate-item-definitions"></a>Öğe tanımlarını değerlendirme

Bu aşamada öğe [tanımları](item-definitions.md) yorumlanır ve bu tanımların bellek içinde gösterimi oluşturulur.

### <a name="evaluate-items"></a>Öğeleri değerlendirme

Hedef içinde tanımlanan öğeler, herhangi bir hedef dışındaki öğelerden farklı şekilde işilir. Bu aşamada, herhangi bir hedefin dışındaki öğeler ve ilişkili meta verileri işlenir.  Öğe tanımları tarafından ayarlanmış meta veriler, öğelerdeki meta veri ayarı tarafından geçersiz kılınır. Öğeler, görünme sırasına göre işlendiğinden, daha önce tanımlanmış olan ancak daha sonra görünen öğelere başvuramayabilirsiniz. Öğeler, özelliklerin geçişinin ardından olduğundan, özellik tanımının daha sonra görüntülendiğinden bağımsız olarak, herhangi bir hedef dışında tanımlanmışsa öğeler herhangi bir özelce erişebilirsiniz.

### <a name="evaluate-usingtask-elements"></a>Öğeleri `UsingTask` değerlendirme

Bu aşamada [UsingTask](usingtask-element-msbuild.md) öğeleri okunur ve görevler yürütme aşamasında daha sonra kullanmak üzere bildirildi.

### <a name="evaluate-targets"></a>Hedefleri değerlendirme

Bu aşamada, yürütme hazırlığı için tüm hedef nesne yapıları bellekte oluşturulur. Gerçek bir yürütme gerçektir. 

## <a name="execution-phase"></a>Yürütme aşaması

Yürütme aşamasında hedefler sıralanmış ve çalıştırıldı ve tüm görevler yürütülür. Ancak ilk olarak, hedefler içinde tanımlanan özellikler ve öğeler, tek bir aşamada bunların görünme sırasıyla birlikte değerlendirilir. İşleme sırası, bir hedefte olmayan özelliklerin ve öğelerin işlenme düzeninden özellikle farklıdır: önce tüm özellikler, sonra da tüm öğeler ayrı geçişler halinde. Bir hedef içindeki özellikler ve öğelerde yapılan değişiklikler, değiştirildikleri hedef sonrasında gözlemlenebilir.

### <a name="target-build-order"></a>Hedef derleme sırası

Tek bir projede hedefler seri olarak yürütülür. Burada önemli olan, bağımlılıkların hedefleri doğru sırada oluşturmak için kullanılacak şekilde her şeyin hangi sırayla derlemek olduğunu belirlemedir.  

Hedef derleme sırası, her hedefte `BeforeTargets` , `DependsOnTargets` ve `AfterTargets` özniteliklerinin kullanımına göre belirlenir. Sonraki hedeflerin sırası, önceki hedef bu özniteliklerde başvurulan bir özelliği değiştiren önceki bir hedefin yürütülmesi sırasında etki altına olabilir.

Sıralama kuralları Hedef derleme siparişini [belirleme konusunda açıklanmıştır.](target-build-order.md#determine-the-target-build-order) İşlem, derleme hedeflerini içeren bir yığın yapısı tarafından belirlenir. Bu görevin en üstünde yer alan hedef yürütmeyi başlatır ve başka bir şeye bağlı ise, bu hedefler yığının en üstüne itilir ve yürütülmaya başlar.  Bağımlılıkları olmayan bir hedef olduğunda, tamamlandıktan sonra yürütülür ve üst hedefi devam eder.

### <a name="project-references"></a>Proje Başvuruları

Burada açıklanan normal yol MSBuild iki kod yolu ve sonraki bölümde açıklanan grafik seçeneği vardır.

Tek tek projeler, öğeler aracılığıyla diğer projelere bağımlılığını `ProjectReference` belirtir. Yığının en üstünde yer alan bir proje, projenin yürütül olduğu noktaya ulaşır ve ortak hedef dosyalarda tanımlanan `ResolveProjectReferences` standart bir hedeftir.

`ResolveProjectReferences`, MSBuild öğelerinin girişleriyle birlikte `ProjectReference` MSBuild görevi çağırır. Öğeler `ProjectReference` gibi yerel öğelere dönüştürüler. `Reference` Yürütme MSBuild (değerlendirme aşaması ilk olarak gerektiğinde yapılır) işlemeye başlarken geçerli proje için yürütme aşaması duraklatılır. Başvurulan proje yalnızca bağımlı projeyi derlemeye başladıktan sonra oluşturur ve bu nedenle bir proje ağacı oluşturur.

Visual Studio çözüm (. sln) dosyalarında proje bağımlılıkları oluşturulmasına izin verir. Bağımlılıklar çözüm dosyasında belirtilir ve yalnızca bir çözüm oluşturulurken veya Visual Studio içinde oluşturulurken dikkate alınır. Tek bir proje oluşturuyorsanız, bu bağımlılık türü yok sayılır. çözüm başvuruları MSBuild tarafından `ProjectReference` öğelere dönüştürülür ve bundan sonra aynı şekilde işlenir.

### <a name="graph-option"></a>Graph seçeneği

Grafik yapı anahtarını (veya) belirtirseniz, `-graphBuild` `-graph` `ProjectReference` MSBuild tarafından kullanılan ilk sınıf kavram olur. MSBuild, tüm projeleri ayrıştırarak, projenin gerçek bağımlılık grafiği olan yapı sırası grafiğini oluşturur ve bu da yapı sırasını belirlemede geçen bir işlem olur. tek tek projelerdeki hedeflerde olduğu gibi MSBuild, başvurulan projelerin bağımlı oldukları projelerden sonra oluşturulduğundan emin olur.

## <a name="parallel-execution"></a>Paralel yürütme

çok işlemcili destek ( `-maxCpuCount` veya `-m` anahtar) kullanıyorsanız, MSBuild, kullanılabilir CPU çekirdeklerini kullanan MSBuild süreçler olan düğümleri oluşturur. Her proje kullanılabilir bir düğüme gönderilir. Bir düğüm içinde, tek tek proje, yürütme işlem temelli olarak oluşturulur.

Görevler, <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> MSBuild özelliğin değerine göre ayarlanmış bir Boole değişkeni ayarlanarak paralel yürütme için etkinleştirilebilir `$(BuildInParallel)` . Paralel yürütme için etkinleştirilen görevler için, bir çalışma Zamanlayıcı düğümleri yönetir ve işleri düğümlere atar.

Bkz. [MSBuild ile paralel olarak birden çok proje oluşturma](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>Standart içeri aktarmalar

*microsoft. common. props* ve *microsoft. common. targets* , .net proje dosyaları (açıkça veya örtük olarak SDK stili projelere) tarafından içeri aktarılır ve Visual Studio yüklemesinde *MSBuild \current\bin* klasöründe bulunur. C++ projelerinin içeri aktarmalar hiyerarşisi vardır; bkz. [C++ projeleri için MSBuild iç işlevleri](/cpp/build/reference/msbuild-visual-cpp-overview).

*Microsoft. Common. props* dosyası, geçersiz kılabileceğiniz Varsayılanları ayarlar. Proje dosyasının başlangıcında içeri aktarılır (açıkça veya örtük olarak). Bu şekilde, projenizin ayarları varsayılandan sonra görünür, böylece bunları geçersiz kılar.

*Microsoft. Common. targets* dosyası ve içeri aktardığı hedef dosyalar .NET projeleri için standart derleme işlemini tanımlar. Ayrıca, derlemeyi özelleştirmek için kullanabileceğiniz uzantı noktaları da sağlar.

Uygulamasında, *Microsoft. Common. targets* , *Microsoft. Common. CurrentVersion. targets* içeri aktaran bir ince sarmalayıcı. Bu dosya, standart özellikler için ayarları içerir ve yapı sürecini tanımlayan gerçek hedefleri tanımlar. `Build`Hedef burada tanımlanmıştır, ancak aslında boştur. Ancak hedef,, `Build` `DependsOnTargets` ve olan gerçek derleme adımlarını oluşturan tek tek hedefleri belirten özniteliği içerir `BeforeBuild` `CoreBuild` `AfterBuild` . `Build`Hedef aşağıdaki gibi tanımlanır:

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild` ve `AfterBuild` uzantı noktalardır. Bunlar *Microsoft. Common. CurrentVersion. targets* dosyasında boştur, ancak projeler, `BeforeBuild` `AfterBuild` ana yapı işleminden önce veya sonra gerçekleştirilmesi gereken görevlerle kendi ve hedeflerini sağlayabilir. `AfterBuild` , hiçbir işlem yapılmadan önce çalıştırılır, `Build` çünkü `AfterBuild` `DependsOnTargets` Hedefteki özniteliğinde görünür `Build` , ancak bundan sonra gerçekleşir `CoreBuild` .

`CoreBuild`Hedef, derleme araçlarına yapılan çağrıları aşağıda gösterildiği gibi içerir:

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

Aşağıdaki tabloda bu hedefler açıklanmaktadır; Bazı hedefler yalnızca belirli proje türleri için geçerlidir.

| Hedef | Açıklama |
|--------|-------------|
| BuildOnlySettings | Visual Studio tarafından proje yükünde MSBuild çağrıldığında değil yalnızca gerçek derlemeler için Ayarlar. |
| PrepareForBuild | Derleme için önkoşulları hazırlama |
| PreBuildEvent | Derlemeden önce yürütülecek görevleri tanımlamak için projeler için uzantı noktası |
| ResolveProjectReferences | Proje bağımlılıklarını çözümleme ve başvurulan projeleri derleme |
| ResolveAssemblyReferences| Başvurulan derlemeleri bulun. |
| Resolvereferde | `ResolveProjectReferences` `ResolveAssemblyReferences` Tüm bağımlılıkları bulmak için ve içerir |
| PrepareResources | Kaynak dosyalarını işle |
| ResolveKeySource| derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtarını ve [ClickOnce](../deployment/clickonce-security-and-deployment.md) bildirimlerini imzalamak için kullanılan sertifikayı çözün. |
| Se | Derleyiciyi çağırır |
| ExportWindowsMDFile | Derleyici tarafından oluşturulan WinMDModule dosyalarından bir [winmd](/uwp/winrt-cref/winmd-files) dosyası oluşturun. |
| Unmanagedkayıt silme | Önceki bir derlemeden [com birlikte çalışma](/dotnet/standard/native-interop/cominterop) kayıt defteri girdilerini kaldırma/Temizleme |
| GenerateSerializationAssemblies | [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe)kullanarak bir XML serileştirme bütünleştirilmiş kodu oluşturun.|
| CreateSatelliteAssemblies | Kaynaklardaki her benzersiz kültür için bir uydu bütünleştirilmiş kodu oluşturun. |
| Bildirim oluştur | [ClickOnce](../deployment/clickonce-security-and-deployment.md) uygulama ve dağıtım bildirimleri veya yerel bir bildirim oluşturur. |
| GetTargetPath | Bu proje için derleme ürününü (yürütülebilir veya derleme) içeren, meta verilerle bir öğe döndürün. |
| PrepareForRun | Yapı çıktılarını değiştirildiklerinde son dizine kopyalayın. |
| UnmanagedRegistration | [Com birlikte çalışması](/dotnet/standard/native-interop/cominterop) için kayıt defteri girişlerini ayarlama |
| IncrementalClean | Önceki bir derlemede üretilen ancak geçerli derlemede üretilmeyen dosyaları kaldırın. Bu, `Clean` artımlı derlemelerde iş yapmak için gereklidir. |
| PostBuildEvent | Derlemeden sonra çalıştırılacak görevleri tanımlamak için projeler için uzantı noktası |

Önceki tabloda bulunan hedeflerin birçoğu, *Microsoft. CSharp. targets* gibi dile özgü içeri aktarmalar içinde bulunur. Bu dosya, C# .NET projeleri için standart derleme işlemindeki adımları tanımlar. Örneğin, `Compile` aslında C# derleyicisini çağıran hedefi içerir.

## <a name="user-configurable-imports"></a>Kullanıcı tarafından yapılandırılabilir içeri aktarmalar

Standart içeri aktarmalara ek olarak, yapı sürecini özelleştirmek için ekleyebileceğiniz birkaç içeri aktarma vardır.

- *Directory. Build. props*
- *Directory. Build. targets*

Bu dosyalar, içindeki herhangi bir alt klasördeki herhangi bir proje için standart içeri aktarmalar tarafından okundu. Bu, genellikle Çözümdeki tüm projeleri denetlemek için ayarlar için çözüm düzeyinde olur, ancak sürücünün köküne kadar dosya sisteminde de daha yüksek olabilir.

*Directory. Build. props* dosyası *Microsoft. Common. props* tarafından içeri aktarıldığından, tanımlanan özellikler proje dosyasında kullanılabilir. Proje temelinde değerleri özelleştirmek için proje dosyasında yeniden tanımlanabilir. *Dizin. Build. targets* dosyası, proje dosyasından sonra okundu. Genellikle hedefleri içerir, ancak burada tek tek projelerin yeniden tanımlamayı istemediğiniz özellikleri de tanımlayabilirsiniz.

## <a name="customizations-in-a-project-file"></a>Proje dosyasındaki özelleştirmeler

Visual Studio, **Çözüm Gezgini**, **özellikler** penceresinde veya **Project özelliklerde** değişiklik yaparken proje dosyalarınızı güncelleştirir, ancak proje dosyasını doğrudan düzenleyerek kendi değişikliklerinizi de yapabilirsiniz.

birçok yapı davranışı, proje ve çözümlerin tüm klasörlerinin genel olarak özellikleri ayarlamak için, bir projeye yerel ayarlar için proje dosyasında ya da önceki bölümde bahsedilerek bir *dizin. build. props* dosyası oluşturularak MSBuild yapılandırılabilir. Komut satırında veya betiklerdeki geçici derlemeler için, `/p` belirli bir MSBuild çağrısı için özellikleri ayarlamak üzere komut satırındaki seçeneğini de kullanabilirsiniz. ayarlayabileceğiniz özellikler hakkında bilgi için bkz. [ortak MSBuild proje özellikleri](common-msbuild-project-properties.md) .

## <a name="next-steps"></a>Sonraki adımlar

MSBuild işlemi, burada açıklananlar dışında birkaç başka uzantı noktasına sahiptir. Bkz. [yapınızı özelleştirme](customize-your-build.md). [Visual Studio yapı sürecini genişletir](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Ayrıca bkz.

[MSBuild](msbuild.md)
