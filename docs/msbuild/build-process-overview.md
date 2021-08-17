---
title: MSBuild nasıl proje oluşturur
description: Visual Studio veya bir komut satırı ya da komut dosyasından çağrılıp çağrılmayacağı MSBuild proje dosyalarınızı nasıl işleyerek öğrenin.
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
ms.openlocfilehash: 2c5d8a602ffaaefb17480b9f64de9c49a992db500ed5a0cebc00098f6ac34c04
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397962"
---
# <a name="how-msbuild-builds-projects"></a>MSBuild nasıl proje oluşturur

MSBuild aslında nasıl çalışır? bu makalede, MSBuild Visual Studio veya bir komut satırı ya da betikten sonra proje dosyalarınızı nasıl işleyeceği hakkında bilgi edineceksiniz. MSBuild nasıl çalıştığını bilmek, sorunları daha iyi tanılamanıza ve derleme işleminizi daha iyi özelleştirmenize yardımcı olabilir. Bu makalede, derleme süreci açıklanmakta ve büyük ölçüde tüm proje türleri için uygulanabilir.

Tüm derleme süreci, projeyi oluşturan hedeflerin ve görevlerin [ilk başlatma](#startup), [değerlendirme](#evaluation-phase)ve [yürütme](#execution-phase) bilgisinden oluşur. Bu girdilerin yanı sıra, dış içeri aktarmalar, çözüm veya proje düzeyinde *Microsoft. Common. targets* ve [Kullanıcı tarafından yapılandırılabilen içeri aktarmalar](#user-configurable-imports) gibi [Standart içeri aktarmalar](#standard-imports) da dahil olmak üzere yapı işleminin ayrıntılarını tanımlar.

## <a name="startup"></a>Başlangıç

MSBuild, *Microsoft.Build.dll* MSBuild nesne modeli aracılığıyla Visual Studio çağrılabilir veya yürütülebilir dosya doğrudan komut satırında veya cı sistemlerinde olduğu gibi bir betikte çağrılabilir. her iki durumda da, yapı işlemini etkileyen girişler proje dosyası (veya Visual Studio iç proje nesnesi), muhtemelen bir çözüm dosyası, ortam değişkenleri ve komut satırı anahtarları veya nesne modeli eşdeğerleri içerir. başlangıç aşamasında, komut satırı seçenekleri veya nesne modeli eşdeğerleri, günlüğe kaydetme cihazlarını yapılandırma gibi MSBuild ayarları yapılandırmak için kullanılır. Veya anahtarını kullanarak komut satırında ayarlanan özellikler `-property` `-p` Genel özellikler olarak ayarlanır ve proje dosyaları daha sonra okunsa bile proje dosyalarında ayarlanacak tüm değerleri geçersiz kılar.

Sonraki bölümlerde, çözüm dosyaları veya proje dosyaları gibi giriş dosyaları hakkında bilgi verilmektedir.

### <a name="solutions-and-projects"></a>Çözümler ve projeler

MSBuild örnekleri bir projeden veya bir çözümün parçası olarak birçok projeden oluşabilir. çözüm dosyası bir MSBuild XML dosyası değildir, ancak bu dosyayı verilen yapılandırma ve platform ayarları için oluşturulması gereken tüm projeleri bildirmek üzere yorumlar MSBuild. MSBuild bu XML girişini işlediğinde çözüm derlemesi olarak adlandırılır. Her çözüm derlemesinde bir şey çalıştırmanızı sağlayan bazı Genişletilebilir noktalara sahiptir, ancak bu derleme bireysel proje Derlemeleriyle ayrı bir çalıştırma olduğundan, çözüm derlemeden hiçbir özellik veya hedef tanım ayarı her proje derlemesi için uygun değildir.

Çözüm yapısını [Özelleştirme](customize-your-build.md#customize-the-solution-build)konusunda çözüm derlemesini nasıl genişletebileceğinizi öğrenebilirsiniz.

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio derlemeleri ve MSBuild.exe yapılarını karşılaştırma

Visual Studio ' de projelerin ne zaman derlenmesi arasında bazı önemli farklılıklar vardır. MSBuild çalıştırılabiliri aracılığıyla ya da bir derlemeyi başlatmak için MSBuild nesne modelini kullanırken MSBuild doğrudan çağırdığınızda. Visual Studio, Visual Studio derlemeler için proje derleme sırasını yönetir; yalnızca tek bir proje düzeyinde MSBuild çağırır ve ne zaman, MSBuild ne olduğunu önemli ölçüde etkileyen birkaç boole özelliği ( `BuildingInsideVisualStudio` , `BuildProjectReferences` ) ayarlanır. her projenin içinde yürütme, MSBuild ile çağrıldığında aynı olur, ancak başvurulan projelerle aradaki fark oluşur. MSBuild, başvurulan projeler gerekli olduğunda, aslında bir yapı oluşur; diğer bir deyişle, görevleri ve araçları çalıştırır ve çıktıyı oluşturur. Visual Studio derlemesi başvurulan bir projeyi bulduğunda, MSBuild yalnızca başvurulan projeden beklenen çıktıları döndürür; Visual Studio diğer projelerin oluşturulmasını denetlemenize olanak tanır. Visual Studio, derleme sırasını belirler ve tamamen Visual Studio denetimi altında tamamen MSBuild olarak (gerektiğinde) çağırır.

MSBuild bir çözüm dosyasıyla çağrıldığında MSBuild çözüm dosyasını ayrıştırır, standart bir XML giriş dosyası oluşturur, değerlendirir ve projeyi bir proje olarak yürütür. Çözüm derlemesi herhangi bir projeden önce yürütülür. Visual Studio oluşturulurken bu durum gerçekleşmediği halde, MSBuild çözüm dosyasını hiçbir şekilde görmez. Sonuç olarak, çözüm yapı özelleştirmesi (daha önce kullanarak) *. SolutionName. sln. targets* ve *After. solutionname. sln. targets*) yalnızca MSBuild.exe veya nesne modeli temelli, Visual Studio derlemeleri için geçerlidir.

### <a name="project-sdks"></a>Proje SDK’leri

MSBuild proje dosyaları için SDK özelliği nispeten yenidir. Bu değişiklikten önce proje dosyaları, belirli bir proje türü için yapı işlemini tanımlayan *. targets* ve *. props* dosyalarını açıkça içeri aktarmıştır.

.NET Core projeleri, .NET SDK 'nın bunlara uygun sürümünü içeri aktarır. Bkz. genel bakış, [.NET Core proje SDK 'ları](/dotnet/core/project-sdk/overview)ve [özelliklere](/dotnet/core/project-sdk/msbuild-props)başvuru.

## <a name="evaluation-phase"></a>Değerlendirme aşaması

Bu bölümde, ne yapılacağını belirlemek için bellek içi nesneler oluşturmak üzere bu giriş dosyalarının nasıl işlendiği ve ayrıştırılabileceği açıklanmaktadır.

Değerlendirme aşamasının amacı, giriş XML dosyalarına ve yerel ortama göre bellekte nesne yapıları oluşturmaktır. Değerlendirme aşaması, proje XML dosyaları veya gibi giriş dosyalarını ve genel olarak *. props* veya *. targets* dosyaları olarak adlandırılan, birincil olarak Özellikler ayarlayıp tanımlamadığınıza veya yapı hedeflerini tanımlamaya bağlı olarak, içeri aktarılan xml dosyalarını işleyen altı geçişinden oluşur. Her Pass, projeleri oluşturmak için yürütme aşamasında daha sonra kullanılan bellek içi nesnelerin bir parçasını oluşturur, ancak değerlendirme aşamasında gerçek derleme eylemleri gerçekleşmez. Her geçişte, öğeler göründükleri sırada işlenir.

Değerlendirme aşamasındaki geçişler aşağıdaki gibidir:

- Ortam değişkenlerini değerlendir
- İçeri aktarmaları ve özellikleri değerlendir
- Öğe tanımlarını değerlendir
- Öğeleri değerlendir
- [UsingTask](usingtask-element-msbuild.md) öğelerini değerlendir
- Hedefleri değerlendir

Bu geçişlerinin sırası önemli etkilere sahiptir ve proje dosyasını özelleştirirken bilmek önemlidir. Bkz. [özellik ve öğe değerlendirme sırası](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Ortam değişkenlerini değerlendir

Bu aşamada, eşdeğer özellikleri ayarlamak için ortam değişkenleri kullanılır. Örneğin, PATH ortam değişkeni bir özellik olarak kullanılabilir hale getirilir `$(PATH)` . komut satırından veya bir betikten çalıştırıldığında, komut ortamı normal olarak kullanılır ve Visual Studio çalıştırıldığında, Visual Studio başlatıldığında geçerli olan ortam kullanılır.

### <a name="evaluate-imports-and-properties"></a>İçeri aktarmaları ve özellikleri değerlendir

Bu aşamada, proje dosyaları ve tüm içeri aktarma zinciri dahil olmak üzere tüm giriş XML 'SI okundu. MSBuild, projenin ve tüm içeri aktarılan dosyaların xml 'sini temsil eden bellek içi bir xml yapısı oluşturur. Şu anda, hedeflerde olmayan özellikler değerlendirilir ve ayarlanır.

tüm XML giriş dosyalarını kendi sürecinde erken okuma MSBuild bir sonucu olarak, derleme işlemi sırasında bu girdilerde yapılan değişiklikler geçerli derlemeyi etkilemez.

Herhangi bir hedefin dışındaki özellikler, hedefler içindeki özelliklerden farklı şekilde işlenir. Bu aşamada, yalnızca herhangi bir hedefin dışında tanımlanan özellikler değerlendirilir.

Özellikler geçişte sırayla işlendiği için, girişte herhangi bir noktada bir özellik girişte daha önce görünen özellik değerlerine erişebilir, ancak daha sonra görünen özellikler değildir.

Öğeler değerlendirilmeden önce Özellikler işlendiği için, Özellikler geçişinin herhangi bir parçası boyunca hiçbir öğenin değerine erişemezsiniz. 

### <a name="evaluate-item-definitions"></a>Öğe tanımlarını değerlendir

Bu aşamada, [öğe tanımları](item-definitions.md) yorumlanır ve bu tanımların bellek içi temsili oluşturulur.

### <a name="evaluate-items"></a>Öğeleri değerlendir

Bir hedefin içinde tanımlanan öğeler, herhangi bir hedef dışındaki öğelerden farklı şekilde işlenir. Bu aşamada, herhangi bir hedefin dışındaki öğeler ve ilgili meta verileri işlenir.  Öğe tanımlarına göre ayarlanan meta veriler, öğelerdeki meta veri ayarı tarafından geçersiz kılınır. Öğeler göründükleri sırada işlendiği için, daha önce tanımlanmış olan ancak daha sonra görünmeyen öğelere başvurabilirsiniz. Öğeler, Özellikler başarılı olduktan sonra, özellik tanımının daha sonra görünüp başlatılmayacağını fark etmeksizin herhangi bir hedefin dışında tanımlanmışsa öğeler herhangi bir özelliğe erişebilir.

### <a name="evaluate-usingtask-elements"></a>`UsingTask`Öğeleri değerlendir

Bu aşamada, [görev](usingtask-element-msbuild.md) öğeleri okunabilir ve görevler, yürütme aşamasında daha sonra kullanılmak üzere bildirilmiştir.

### <a name="evaluate-targets"></a>Hedefleri değerlendir

Bu aşamada, yürütme hazırlığı sırasında, tüm hedef nesne yapıları bellekte oluşturulur. Gerçek yürütme gerçekleşmez. 

## <a name="execution-phase"></a>Yürütme aşaması

Yürütme aşamasında, hedefler sıralanır ve çalıştırılır ve tüm görevler yürütülür. Ancak ilki, hedefler içinde tanımlanan özellikler ve öğeler göründükleri sırada tek bir aşamada birlikte değerlendirilir. İşlem sırası, özellik ve bir hedefte olmayan öğelerin nasıl işlendiği konusunda özellikle farklıdır: önce tüm özellikler, sonra tüm öğeler ayrı geçişlerinde. Bir hedef içindeki özelliklerde ve öğelerde yapılan değişiklikler değiştirildikleri hedeften sonra gözlemlenebilir.

### <a name="target-build-order"></a>Hedef derleme sırası

Tek bir projede, hedefler işlem temelli olarak yürütülür. Merkezi sorun, hedefleri doğru sırada oluşturmak için bağımlılıkların kullanılması amacıyla her şeyi hangi sırayla derleyeceğini belirleme ' dir.  

Hedef derleme sırası `BeforeTargets` , her bir hedefte,, `DependsOnTargets` ve özniteliklerinin kullanımıyla belirlenir `AfterTargets` . Daha önceki hedef, bu özniteliklerde başvurulan bir özelliği değiştirirse, daha sonraki hedeflerin sırası daha önceki bir hedefin yürütülmesi sırasında etkilenebilir.

Sıralama kuralları, [hedef derleme sırasını belirlemede](target-build-order.md#determine-the-target-build-order)açıklanmıştır. İşlem, Derlenecek hedefleri içeren bir yığın yapısına göre belirlenir. Bu görevin en üstündeki hedef yürütme başlar ve başka herhangi bir şeye bağımlıysa, bu hedefler yığının en üstüne itilir ve yürütülmeye başlarlar.  Hiçbir bağımlılığı olmayan bir hedef olduğunda, tamamlanma ve üst hedef özgeçmişler için yürütülür.

### <a name="project-references"></a>Proje Başvuruları

MSBuild iki kod yolu vardır. bu, normal bir, ve sonraki bölümde açıklanan graph seçeneğidir.

Bireysel projeler, diğer projelere öğeler aracılığıyla bağımlılığını belirler `ProjectReference` . Yığının en üstündeki bir proje oluşturmaya başladığında, `ResolveProjectReferences` ortak hedef dosyalarında tanımlanmış standart bir hedef olan hedefin çalıştırıldığı noktaya ulaşır.

`ResolveProjectReferences`MSBuild görevini, `ProjectReference` çıkışları almak için öğelerin girişleri ile çağırır. `ProjectReference`Öğeler gibi yerel öğelere dönüştürülür `Reference` . geçerli proje için MSBuild yürütme aşaması, yürütme aşaması başvurulan projeyi işlemeye başladığında duraklatılır. (değerlendirme aşaması öncelikle gerektiği şekilde yapılır). Başvurulan proje yalnızca bağımlı projeyi oluşturmaya başladıktan sonra oluşturulur ve bu sayede proje oluşturan projeler ağacı oluşturulur.

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
