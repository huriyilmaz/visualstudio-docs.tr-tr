---
title: Visual Studio Tümleştirmesi (MSBuild)
titleSuffix: ''
description: Farklı araçlar tarafından yazılmış ve özelleştirilmiş derleme işlemlerine sahip olsalar bile, Visual Studio 'Nun projeleri MSBuild biçiminde nasıl barındırabilecekleri hakkında bilgi edinin.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17cb665d1b5ae399647868652f2b1e73fcd4543e
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046680"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio tümleştirmesi (MSBuild)

Visual Studio, yönetilen projeleri yüklemek ve derlemek için MSBuild barındırır. MSBuild projeden sorumlu olduğundan, proje farklı bir araç tarafından yazılmış ve özelleştirilmiş bir yapı işlemine sahip olsa bile, MSBuild biçimindeki neredeyse tüm projeler Visual Studio 'da başarılı bir şekilde kullanılabilir.

 Bu makalede, Visual Studio 'nun, Visual Studio 'da yüklemek ve derlemek istediğiniz projeleri ve *. targets* dosyalarını özelleştirirken göz önünde bulundurmanız gereken, Visual Studio 'nun MSBuild barındırmanın belirli yönleri açıklanmaktadır. Bunlar, IntelliSense ve hata ayıklama gibi Visual Studio özelliklerinin özel projeniz için çalışması konusunda emin olmanıza yardımcı olur.

 C++ projeleri hakkında daha fazla bilgi için bkz. [proje dosyaları](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Proje dosya adı uzantıları

 *MSBuild.exe* , düzeniyle eşleşen herhangi bir proje dosya adı uzantısını tanır *. \* PROJ* . Ancak, Visual Studio yalnızca projeyi yükleyecek dile özgü proje sistemini belirleyen bu proje dosya adı uzantılarının bir alt kümesini tanır. Visual Studio 'Nun dilden bağımsız MSBuild tabanlı proje sistemi yoktur.

 Örneğin, C# proje sistemi *. csproj* dosyalarını yükler, ancak Visual Studio bir *. xxproj* dosyasını yükleyemez. Rastgele bir dildeki kaynak dosyaları için bir proje dosyası, Visual Studio 'da yüklenecek Visual Basic veya C# proje dosyaları ile aynı uzantıyı kullanmalıdır.

## <a name="well-known-target-names"></a>İyi bilinen hedef adları

 Visual Studio 'daki **Build** komutuna tıkladığınızda, projede varsayılan hedef yürütülür. Genellikle, bu hedef de olarak adlandırılır `Build` . **Yeniden oluşturma** veya **Temizleme** komutunun seçilmesi, projede aynı ada sahip bir hedefi yürütmeye çalışır. **Yayımla** ' ya tıkladığınızda projede adlı bir hedef yürütülür `PublishOnly` .

## <a name="configurations-and-platforms"></a>Yapılandırma ve platformlar

 Konfigürasyonlar, bir özniteliği içeren bir öğede gruplanmış özelliklere göre MSBuild projelerinde temsil edilir `PropertyGroup` `Condition` . Visual Studio, görüntülenecek proje yapılandırmalarının ve platformların bir listesini oluşturmak için bu koşullara bakar. Bu listeyi başarıyla ayıklamak için, koşulların aşağıdakine benzer bir biçimi olmalıdır:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio `PropertyGroup` , bu amaçla,,, `ItemGroup` `Import` özelliği ve öğe öğelerinde yer alan koşullara bakar.

## <a name="additional-build-actions"></a>Ek derleme eylemleri

 Visual Studio, bir projedeki dosyanın öğe türü adını **dosya özellikleri** penceresinin **Build Action** özelliği ile değiştirmenize olanak sağlar. **Derleme** , **EmbeddedResource** , **içerik** ve **none** öğe türü adları her zaman projenizde olan diğer öğe türü adlarıyla birlikte bu menüde listelenir. Bu menüde her zaman özel öğe türü adlarının kullanılabilir olduğundan emin olmak için adları adlı bir öğe türüne ekleyebilirsiniz `AvailableItemName` . Örneğin, proje dosyanıza aşağıdakileri eklemek, özel tür **JScript** 'i içeri aktarılan tüm projeler için bu menüye ekler:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Bazı öğe türü adları, Visual Studio için özeldir ancak bu açılan menüde listelenmez.

## <a name="in-process-compilers"></a>İşlem içi derleyiciler

 Mümkün olduğunda Visual Studio, daha fazla performans için Visual Basic derleyicisinin işlem içi sürümünü kullanmayı dener. (C# için geçerli değildir.) Bunun düzgün çalışması için aşağıdaki koşulların karşılanması gerekir:

- Projenin bir hedefinde, Visual Basic projeleri için adlı bir görev olmalıdır `Vbc` .

- `UseHostCompilerIfAvailable`Görevin parametresi true olarak ayarlanmalıdır.

## <a name="design-time-intellisense"></a>Tasarım zamanı IntelliSense

 Derleme bir çıkış derlemesi oluşturmadan önce Visual Studio 'da IntelliSense desteği almak için aşağıdaki koşulların karşılanması gerekir:

- Adında bir hedef olması gerekir `Compile` .

- `Compile`Hedefi veya bağımlılıklarından biri, proje için ya da gibi derleyici görevini çağırmalıdır `Csc` `Vbc` .

- `Compile`Hedefi veya bağımlılıklarından biri, derleyicinin IntelliSense için gereken tüm parametreleri, özellikle de tüm başvuruları almasına neden olmalıdır.

- [Işlem içi derleyiciler](#in-process-compilers) bölümünde listelenen koşullar sağlanmalıdır.

## <a name="build-solutions"></a>Çözüm oluşturma

 Visual Studio 'da çözüm dosyası ve proje derleme sıralaması, Visual Studio 'Nun kendisi tarafından denetlenir. Komut satırında *msbuild.exe* bir çözüm oluştururken, MSBuild çözüm dosyasını ayrıştırır ve proje yapılarını sıralar. Her iki durumda da, projeler bağımlılık sırasında tek tek oluşturulmuştur ve proje başvurularına proje başvurularına verilmez. Buna karşılık, tek tek projeler *msbuild.exe* ile oluşturulduğunda proje başvurularına proje başvurularına çapraz yapılır.

 Visual Studio içinde derlerken, özelliği `$(BuildingInsideVisualStudio)` olarak ayarlanır `true` . Bu, projede veya *. targets* dosyalarında, derleme 'in farklı davranmasına neden olacak şekilde kullanılabilir.

## <a name="display-properties-and-items"></a>Özellikleri ve öğeleri görüntüle

 Visual Studio belirli özellik adlarını ve değerlerini tanır. Örneğin, bir projedeki aşağıdaki özellik, **Windows uygulamasının** **Proje Tasarımcısı** 'ndaki **uygulama türü** kutusunda görünmesine neden olur.

```xml
<OutputType>WinExe</OutputType>
```

 Özellik değeri **Proje tasarımcısında** düzenlenebilir ve proje dosyasına kaydedilebilir. Bu tür bir özelliğe el ile düzenleyerek geçersiz bir değer verilirse, proje yüklendiğinde Visual Studio bir uyarı gösterir ve geçersiz değeri varsayılan bir değerle değiştirir.

 Visual Studio bazı özellikler için Varsayılanları anlamıştır. Bu özellikler, varsayılan olmayan değerlere sahip olmadıkları takdirde proje dosyasında kalıcı olmayacaktır.

 Rastgele adlara sahip özellikler Visual Studio 'da gösterilmez. Visual Studio 'daki rastgele özellikleri değiştirmek için, proje dosyasını XML düzenleyicisinde açmanız ve bunları el ile düzenlemeniz gerekir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki [Visual Studio 'da proje dosyalarını düzenleme](#edit-project-files-in-visual-studio) bölümüne bakın.

 Projesinde, rastgele öğe türü adlarıyla tanımlanmış öğeler, varsayılan olarak, Proje düğümleri altında **Çözüm Gezgini** görüntülenir. Bir öğeyi görüntüleme listesinden gizlemek için `Visible` meta verileri olarak ayarlayın `false` . Örneğin, aşağıdaki öğe derleme işlemine katılır, ancak **Çözüm Gezgini** gösterilmez.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> `Visible`Meta veriler, C++ projeleri için **Çözüm Gezgini** yok sayılır. Öğeler, false olarak ayarlanmış olsa bile her zaman gösterilir `Visible` .

 Projeye içeri aktarılan dosyalarda belirtilen öğeler varsayılan olarak görüntülenmez. Yapı işlemi sırasında oluşturulan öğeler **Çözüm Gezgini** hiçbir şekilde gösterilmez.

## <a name="conditions-on-items-and-properties"></a>Öğeler ve özellikler ile ilgili koşullar

 Bir derleme sırasında tüm koşullar tam olarak işlenir.

 Görüntülenecek özellik değerlerini belirlerken, Visual Studio 'Nun yapılandırmaya bağımlı olduğunu düşündüğü özellikler, yapılandırmayı birbirinden bağımsız olarak kabul eden özelliklerden farklı şekilde değerlendirilir. Yapılandırmaya bağımlı olduğunu düşündüğü özellikler için, Visual Studio, `Configuration` ve `Platform` özelliklerini uygun şekilde ayarlar ve MSBuild 'i projeyi yeniden değerlendirmeye yönlendirir. Yapılandırmayı bağımsız olarak kabul eden özellikler için, koşulların nasıl değerlendirileceğini belirsiz hale gelir.

 Öğelerin **Çözüm Gezgini** gösterilip gösterilmeyeceğine karar vermek amacıyla öğelerdeki Koşullu ifadeler her zaman göz ardı edilir.

## <a name="debugging"></a>Hata Ayıklama

 Çıkış derlemesini bulup başlatmak ve hata ayıklayıcıyı iliştirmek için, Visual Studio 'Nun özelliklerine `OutputPath` `AssemblyName` ve `OutputType` doğru şekilde tanımlanmasını gerektirir. Derleme işlemi derleyicinin bir *. pdb* dosyası oluşturmasına neden değilse, hata ayıklayıcısı iliştirilemiyor.

## <a name="design-time-target-execution"></a>Tasarım zamanı hedef yürütme

 Visual Studio, bir projeyi yüklediğinde belirli adlarla hedefleri yürütmeye çalışır. Bu hedefler,,, `Compile` `ResolveAssemblyReferences` ve içerir `ResolveCOMReferences` `GetFrameworkPaths` `CopyRunEnvironmentFiles` . Visual Studio bu hedefleri çalıştırarak derleyicinin IntelliSense sağlamak üzere başlatılabilmesini, hata ayıklayıcının başlatılabilmesini ve Çözüm Gezgini ' de görüntülenen başvuruların çözümlenebilmesini sağlar. Bu hedefler yoksa, proje doğru şekilde yüklenir ve oluşturulur ancak Visual Studio 'daki tasarım zamanı deneyimi tam olarak işlevsel olmayacaktır.

## <a name="edit-project-files-in-visual-studio"></a>Visual Studio 'da proje dosyalarını düzenleme

 Bir MSBuild projesini doğrudan düzenlemek için, proje dosyasını Visual Studio XML düzenleyicisinde açabilirsiniz.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için

1. **Çözüm Gezgini** ' de, proje için kısayol menüsünü açın ve ardından **Projeyi Kaldır** ' ı seçin.

     Proje işaretlendi **(kullanılamıyor)** .

2. **Çözüm Gezgini** ' de, kullanılamayan proje için kısayol menüsünü açın ve ardından **Düzenle \<Project File>** ' yi seçin.

     Proje dosyası Visual Studio XML düzenleyicisinde açılır.

3. Proje dosyasını düzenleyin, kaydedin ve ardından kapatın.

4. **Çözüm Gezgini** ' de, kullanılamayan proje için kısayol menüsünü açın ve ardından **projeyi yeniden yükle** ' yi seçin.

## <a name="intellisense-and-validation"></a>IntelliSense ve doğrulama

 Proje dosyalarını düzenlemek için XML düzenleyicisini kullanırken, IntelliSense ve doğrulama MSBuild şema dosyaları tarafından çalıştırılır. Bunlar, *\<Visual Studio installation directory> \Xml\schemas\1010\msbuild* dizininde bulunan şema önbelleğine yüklenir.

 Temel MSBuild türleri, Microsoft. Build *. Core. xsd* ve Visual Studio tarafından kullanılan ortak türlerde tanımlanmıştır, *Microsoft. Build. CommonTypes. xsd* dosyasında tanımlanmıştır. Şemaları, özel öğe türü adları, özellikleri ve görevleri için IntelliSense ve doğrulamaya sahip olacak şekilde özelleştirmek için *Microsoft. Build. xsd* ' yi düzenleyebilir ya da CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Kendi şemanızı oluşturursanız, **Özellikler** penceresini kullanarak bulmak için XML düzenleyicisini yönlendirirsiniz.

## <a name="edit-loaded-project-files"></a>Yüklenen proje dosyalarını Düzenle

 Visual Studio, proje dosyaları ve proje dosyaları tarafından içeri aktarılan dosyaların içeriğini önbelleğe alır. Yüklü bir proje dosyasını düzenlerseniz, Visual Studio değişikliklerin etkili olması için projeyi otomatik olarak yeniden yüklemenizi ister. Ancak, yüklenen bir proje tarafından içeri aktarılan bir dosyayı düzenlerseniz, yeniden yükleme istemi olmaz ve değişikliklerin etkili olması için projeyi el ile kaldırıp yeniden yüklemeniz gerekir.

## <a name="output-groups"></a>Çıkış grupları

 *Microsoft. Common. targets* içinde tanımlanan birçok hedef, veya ile biten adlara sahiptir `OutputGroups` `OutputGroupDependencies` . Visual Studio, proje çıktılarının belirli listelerini almak için bu hedefleri çağırır. Örneğin, hedef, `SatelliteDllsProjectOutputGroup` derleme oluşturulacak tüm uydu derlemelerinin listesini oluşturur. Bu çıktı grupları, proje başvurularına yayımlama, dağıtım ve proje gibi özellikler tarafından kullanılır. Onları tanımlamayan projeler Visual Studio 'da yüklenir ve oluşturulur, ancak bazı özellikler düzgün çalışmayabilir.

## <a name="reference-resolution"></a>Başvuru çözümleme

 Başvuru çözümleme, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. **Özellikler** penceresinde her bir başvurunun ayrıntılı özelliklerini göstermek için, Visual Studio 'nun başvuru çözümlemesini tetiklemesi gerekir. Aşağıdaki listede, üç tür başvuru ve nasıl çözümlendikleri açıklanmaktadır.

- Bütünleştirilmiş kod başvuruları:

   Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveAssemblyReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `ReferencePath` . Bu öğelerin her biri, `Include` başvurunun tam yolunu içeren bir öğe belirtimine (bir öğenin özniteliğinin değeri) sahip olmalıdır. Öğelerin, aşağıdaki yeni meta verilere ek olarak, geçirilen giriş öğelerinden tüm meta verilere sahip olması gerekir:

  - `CopyLocal`, derlemenin çıkış klasörüne kopyalanıp kopyalanmayacağını belirtir, true veya false olarak ayarlayın.

  - `OriginalItemSpec`, başvurunun orijinal öğe belirtimini içeren.

  - `ResolvedFrom`, .NET Framework dizininden çözümlenmişse "{TargetFrameworkDirectory}" olarak ayarlanır.

- COM başvuruları:

   Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveCOMReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `ComReferenceWrappers` . Bu öğelerin her biri, COM başvurusunun birlikte çalışma derlemesine tam yolu içeren bir öğe belirtimine sahip olmalıdır. Öğelerin, aynı ada sahip yeni meta verilere ek olarak,, `CopyLocal` derlemenin çıkış klasörüne kopyalanıp kopyalanmayacağını belirten, true veya false olarak ayarlandığını belirten, içindeki giriş öğelerinden tüm meta verileri olmalıdır.

- Yerel başvurular

   Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveNativeReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `NativeReferenceFile` . Öğelerin, `OriginalItemSpec` başvurunun orijinal öğe belirtimini içeren, adlı yeni bir meta veri parçasına ek olarak, geçirilen giriş öğelerinden tüm meta verilere sahip olması gerekir.

## <a name="performance-shortcuts"></a>Performans kısayolları

 Hata ayıklamayı başlatmak için Visual Studio IDE 'yi kullanırsanız (F5 tuşunu seçerek veya menü çubuğunda **hata**  >  **ayıklamayı Başlat** ' ı seçerek) veya projenizi oluşturmak için (örneğin, **derleme**  >  **çözümü** ), yapı işlemi performansı artırmak için hızlı bir güncelleştirme denetimi kullanır. Özelleştirilmiş yapıların, yerleşik olarak oluşturulan dosyalar oluşturmasındaki bazı durumlarda, hızlı güncelleştirme denetimi değiştirilen dosyaları doğru şekilde tanımlamaz. Daha kapsamlı güncelleştirme denetimleri gerektiren projeler, ortam değişkenini ayarlayarak hızlı denetlemeyi kapatabilir `DISABLEFASTUPTODATECHECK=1` . Alternatif olarak, projeler bunu projede veya projenin içeri aktardığı bir dosyada MSBuild özelliği olarak ayarlayabilir.

 Visual Studio 'daki normal derlemeler için hızlı güncelleştirme denetimi uygulanmaz ve proje, derlemeyi bir komut isteminde çağırırı olarak derler.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Studio derleme işlemini genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [IDE içinden derleme başlatma](../msbuild/starting-a-build-from-within-the-ide.md)
- [.NET Framework uzantılarını Kaydet](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Item öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
