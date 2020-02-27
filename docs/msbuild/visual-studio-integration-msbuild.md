---
title: Visual Studio Tümleştirmesi (MSBuild)
titleSuffix: ''
ms.custom: seodec18
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
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631204"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio tümleştirmesi (MSBuild)

Visual Studio, yönetilen projeleri yüklemek ve derlemek için MSBuild barındırır. MSBuild projeden sorumlu olduğundan, proje farklı bir araç tarafından yazılmış ve özelleştirilmiş bir yapı işlemine sahip olsa bile, MSBuild biçimindeki neredeyse tüm projeler Visual Studio 'da başarılı bir şekilde kullanılabilir.

 Bu makalede, Visual Studio 'nun, Visual Studio 'da yüklemek ve derlemek istediğiniz projeleri ve *. targets* dosyalarını özelleştirirken göz önünde bulundurmanız gereken, Visual Studio 'nun MSBuild barındırmanın belirli yönleri açıklanmaktadır. Bunlar, IntelliSense ve hata ayıklama gibi Visual Studio özelliklerinin özel projeniz için çalışması konusunda emin olmanıza yardımcı olur.

 Projeler hakkında C++ daha fazla bilgi için bkz. [proje dosyaları](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Proje dosya adı uzantıları

 *MSBuild. exe* , düzeniyle eşleşen herhangi bir proje dosya adı uzantısını tanır *.\*proj*. Ancak, Visual Studio yalnızca projeyi yükleyecek dile özgü proje sistemini belirleyen bu proje dosya adı uzantılarının bir alt kümesini tanır. Visual Studio 'Nun dilden bağımsız MSBuild tabanlı proje sistemi yoktur.

 Örneğin, C# proje sistemi *. csproj* dosyalarını yükler, ancak Visual Studio bir *. xxproj* dosyasını yükleyemez. Rastgele bir dildeki kaynak dosyaları için bir proje dosyası, Visual Studio 'da yüklenecek Visual Basic veya C# proje dosyaları ile aynı uzantıyı kullanmalıdır.

## <a name="well-known-target-names"></a>İyi bilinen hedef adları

 Visual Studio 'daki **Build** komutuna tıkladığınızda, projede varsayılan hedef yürütülür. Genellikle, bu hedef de `Build`olarak adlandırılır. **Yeniden oluşturma** veya **Temizleme** komutunun seçilmesi, projede aynı ada sahip bir hedefi yürütmeye çalışır. **Yayımla** ' ya tıkladığınızda, projede `PublishOnly` adlı bir hedef yürütülür.

## <a name="configurations-and-platforms"></a>Yapılandırmalar ve platformlar

 Konfigürasyonlar, bir `Condition` özniteliği içeren `PropertyGroup` öğesinde gruplanmış Özellikler tarafından MSBuild projelerinde temsil edilir. Visual Studio, görüntülenecek proje yapılandırmalarının ve platformların bir listesini oluşturmak için bu koşullara bakar. Bu listeyi başarıyla çıkarmak için koşulların aşağıdakine benzer bir biçimde olmalıdır:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio, bu amaçla `PropertyGroup`, `ItemGroup`, `Import`, özellik ve öğe öğelerinde yer alan koşullara bakar.

## <a name="additional-build-actions"></a>Ek yapı eylemleri

 Visual Studio, bir projedeki dosyanın öğe türü adını **dosya özellikleri** penceresinin **Build Action** özelliği ile değiştirmenize olanak sağlar. **Derleme**, **EmbeddedResource**, **içerik**ve **none** öğe türü adları her zaman projenizde olan diğer öğe türü adlarıyla birlikte bu menüde listelenir. Bu menüde her zaman özel öğe türü adlarının kullanılabilir olduğundan emin olmak için, adları `AvailableItemName`adlı bir öğe türüne ekleyebilirsiniz. Örneğin, proje dosyanıza aşağıdakileri eklemek, özel tür **JScript** 'i içeri aktarılan tüm projeler için bu menüye ekler:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Bazı öğe türü adları, Visual Studio için özeldir ancak bu açılan menüde listelenmez.

## <a name="in-process-compilers"></a>İşlem içi derleyiciler

 Mümkün olduğunda Visual Studio, daha fazla performans için Visual Basic derleyicisinin işlem içi sürümünü kullanmayı dener. (İçin C#geçerli değildir.) Bunun düzgün çalışması için aşağıdaki koşulların karşılanması gerekir:

- Projenin bir hedefinde, Visual Basic projeleri için `Vbc` adlı bir görev olmalıdır.

- Görevin `UseHostCompilerIfAvailable` parametresi true olarak ayarlanmalıdır.

## <a name="design-time-intellisense"></a>Tasarım zamanı IntelliSense

 Derleme bir çıkış derlemesi oluşturmadan önce Visual Studio 'da IntelliSense desteği almak için aşağıdaki koşulların karşılanması gerekir:

- `Compile`adlı bir hedef olmalıdır.

- `Compile` hedefi ya da bağımlılıklarından biri, proje için `Csc` veya `Vbc`gibi derleyici görevini çağırmalıdır.

- `Compile` hedefi veya bağımlılıklarından biri, derleyicinin IntelliSense için gereken tüm parametreleri, özellikle de tüm başvuruları almasına neden olmalıdır.

- [Işlem içi derleyiciler](#in-process-compilers) bölümünde listelenen koşullar sağlanmalıdır.

## <a name="build-solutions"></a>Çözüm oluşturma

 Visual Studio 'da çözüm dosyası ve proje derleme sıralaması, Visual Studio 'Nun kendisi tarafından denetlenir. MSBuild *. exe* ile komut satırında bir çözüm oluştururken, MSBuild çözüm dosyasını ayrıştırır ve proje yapılarını sıralar. Her iki durumda da projeler ayrı olarak bağımlılık sırasında oluşturulur ve projeden projeye başvurular geçirilmez. Buna karşılık, tek tek projeler *MSBuild. exe*ile oluşturulduğunda proje başvurularına proje başvurularına çapraz bir şekilde eklenir.

 Visual Studio içinde derlerken Özellik `$(BuildingInsideVisualStudio)` `true`olarak ayarlanır. Bu, projede veya *. targets* dosyalarında, derleme 'in farklı davranmasına neden olacak şekilde kullanılabilir.

## <a name="display-properties-and-items"></a>Özellikleri ve öğeleri görüntüleme

 Visual Studio belirli özellik adlarını ve değerlerini tanır. Örneğin, bir projedeki aşağıdaki özellik, **Windows uygulamasının** **Proje Tasarımcısı**'ndaki **uygulama türü** kutusunda görünmesine neden olur.

```xml
<OutputType>WinExe</OutputType>
```

 Özellik değeri **Proje tasarımcısında** düzenlenebilir ve proje dosyasına kaydedilebilir. Bu tür bir özelliğe el ile düzenleyerek geçersiz bir değer verilirse, proje yüklendiğinde Visual Studio bir uyarı gösterir ve geçersiz değeri varsayılan bir değerle değiştirir.

 Visual Studio bazı özellikler için Varsayılanları anlamıştır. Varsayılan olmayan değerleri sahip olmadıkları sürece bu özellik proje dosyasına kalıcı olmaz.

 Rastgele adlara sahip özellikler Visual Studio 'da gösterilmez. Visual Studio 'daki rastgele özellikleri değiştirmek için, proje dosyasını XML düzenleyicisinde açmanız ve bunları el ile düzenlemeniz gerekir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki [Visual Studio 'da proje dosyalarını düzenleme](#edit-project-files-in-visual-studio) bölümüne bakın.

 Projesinde, rastgele öğe türü adlarıyla tanımlanmış öğeler, varsayılan olarak, Proje düğümleri altında **Çözüm Gezgini** görüntülenir. Bir öğeyi ekranda gizlemek için `Visible` meta verilerini `false`olarak ayarlayın. Örneğin, aşağıdaki öğe derleme işlemine katılır, ancak **Çözüm Gezgini**gösterilmez.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> `Visible` meta veriler, projeler C++ için **Çözüm Gezgini** tarafından yok sayılır. `Visible` false olarak ayarlanmış olsa bile, öğeler her zaman gösterilir.

 Projeye aktarılan dosyalarda bildirilen öğeler varsayılan olarak görüntülenmez. Yapı işlemi sırasında oluşturulan öğeler **Çözüm Gezgini**hiçbir şekilde gösterilmez.

## <a name="conditions-on-items-and-properties"></a>Koşullara öğeleri ve özellikleri

 Bir yapı sırasında tüm koşullar tam olarak dikkate alınır.

 Görüntülenecek özellik değerlerini belirlerken, Visual Studio 'Nun yapılandırmaya bağımlı olduğunu düşündüğü özellikler, yapılandırmayı birbirinden bağımsız olarak kabul eden özelliklerden farklı şekilde değerlendirilir. Yapılandırmaya bağımlı olduğunu düşündüğü özellikler için, Visual Studio `Configuration` ve `Platform` özelliklerini uygun şekilde ayarlar ve MSBuild 'i projeyi yeniden değerlendirmeye yönlendirir. Özellikleri yeniden yapılandırma bağımsız olarak, koşulların nasıl değerlendirileceği belirsiz olarak kabul eder.

 Öğelerin **Çözüm Gezgini**gösterilip gösterilmeyeceğine karar vermek amacıyla öğelerdeki Koşullu ifadeler her zaman göz ardı edilir.

## <a name="debugging"></a>Hata ayıklama

 Çıkış derlemesini bulup başlatmak ve hata ayıklayıcıyı iliştirmek için, Visual Studio 'Nun `OutputPath`, `AssemblyName`ve `OutputType` doğru tanımlanmış özellikler olması gerekir. Derleme işlemi derleyicinin bir *. pdb* dosyası oluşturmasına neden değilse, hata ayıklayıcısı iliştirilemiyor.

## <a name="design-time-target-execution"></a>Tasarım zamanı hedef yürütme

 Visual Studio, bir projeyi yüklediğinde belirli adlarla hedefleri yürütmeye çalışır. Bu hedefler `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`ve `CopyRunEnvironmentFiles`içerir. Visual Studio bu hedefleri çalıştırarak derleyicinin IntelliSense sağlamak üzere başlatılabilmesini, hata ayıklayıcının başlatılabilmesini ve Çözüm Gezgini ' de görüntülenen başvuruların çözümlenebilmesini sağlar. Bu hedefler yoksa, proje doğru şekilde yüklenir ve oluşturulur ancak Visual Studio 'daki tasarım zamanı deneyimi tam olarak işlevsel olmayacaktır.

## <a name="edit-project-files-in-visual-studio"></a>Visual Studio'da proje dosyalarını düzenleme

 Bir MSBuild projesini doğrudan düzenlemek için, proje dosyasını Visual Studio XML düzenleyicisinde açabilirsiniz.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için

1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Projeyi Kaldır**' ı seçin.

     Proje işaretlendi **(kullanılamıyor)** .

2. **Çözüm Gezgini**' de, kullanılamayan proje için kısayol menüsünü açın ve **\<proje Dosya > Düzenle**' yi seçin.

     Proje dosyası Visual Studio XML Düzenleyicisi'nde açılır.

3. Düzenleyin, kaydedin ve ardından Proje dosyasını kapatın.

4. **Çözüm Gezgini**' de, kullanılamayan proje için kısayol menüsünü açın ve ardından **projeyi yeniden yükle**' yi seçin.

## <a name="intellisense-and-validation"></a>IntelliSense ve doğrulama

 Proje dosyalarını düzenlemek için XML düzenleyicisini kullanırken, IntelliSense ve doğrulama MSBuild şema dosyaları tarafından çalıştırılır. Bunlar, *\<Visual Studio yükleme dizini > \Xml\schemas\10\msbuild*dizininde bulunan şema önbelleğine yüklenir.

 Temel MSBuild türleri, Microsoft. Build *. Core. xsd* ve Visual Studio tarafından kullanılan ortak türlerde tanımlanmıştır, *Microsoft. Build. CommonTypes. xsd*dosyasında tanımlanmıştır. Şemaları, özel öğe türü adları, özellikleri ve görevleri için IntelliSense ve doğrulamaya sahip olacak şekilde özelleştirmek için *Microsoft. Build. xsd*' yi düzenleyebilir ya da CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Kendi şemanızı oluşturursanız, **Özellikler** penceresini kullanarak bulmak için XML düzenleyicisini yönlendirirsiniz.

## <a name="edit-loaded-project-files"></a>Yüklenmiş proje dosyalarını düzenleme

 Visual Studio, proje dosyaları ve proje dosyaları tarafından içeri aktarılan dosyaların içeriğini önbelleğe alır. Yüklü bir proje dosyasını düzenlerseniz, Visual Studio değişikliklerin etkili olması için projeyi otomatik olarak yeniden yüklemenizi ister. Ancak yüklenmiş bir proje tarafından içe aktarılan bir dosyayı düzenlerseniz, herhangi bir yeniden yükleme istemi olmayacaktır ve kaldırma ve değişikliklerin etkili el ile yapmak için projeyi yeniden yükleyin.

## <a name="output-groups"></a>Çıkış grupları

 *Microsoft. Common. targets* içinde tanımlanan birçok hedefin adı `OutputGroups` veya `OutputGroupDependencies`bitiyor. Visual Studio, proje çıktılarının belirli listelerini almak için bu hedefleri çağırır. Örneğin `SatelliteDllsProjectOutputGroup` hedefi, bir derlemenin oluşturulacağı tüm uydu derlemelerinin bir listesini oluşturur. Bu çıktı grupları yayımlama, dağıtım ve projeden projeye başvurular gibi özellikler tarafından kullanılır. Onları tanımlamayan projeler Visual Studio 'da yüklenir ve oluşturulur, ancak bazı özellikler düzgün çalışmayabilir.

## <a name="reference-resolution"></a>Başvuru çözümleme

 Başvuru çözümleme, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. **Özellikler** penceresinde her bir başvurunun ayrıntılı özelliklerini göstermek için, Visual Studio 'nun başvuru çözümlemesini tetiklemesi gerekir. Aşağıdaki liste, üç başvuru türünü ve bunların nasıl kullanıldığını açıklar.

- Bütünleştirilmiş kod başvuruları:

   Proje sistemi, `ResolveAssemblyReferences`iyi bilinen ada sahip bir hedef çağırır. Bu hedef, `ReferencePath`öğe türü adına sahip öğeler üretmelidir. Bu öğelerin her biri, başvurunun tam yolunu içeren bir öğe belirtimine (bir öğenin `Include` özniteliğinin değeri) sahip olmalıdır. Öğeleri aracılığıyla aşağıdaki yeni meta veriler ek olarak geçirilen girdi öğelerinin tüm meta verilerine sahip olmanız gerekir:

  - `CopyLocal`, derlemenin çıkış klasörüne kopyalanıp kopyalanmayacağını, true veya false olarak ayarlandığını gösterir.

  - başvurunun özgün öğe belirtimini içeren `OriginalItemSpec`.

  - `ResolvedFrom`, .NET Framework dizininden çözümlenmişse "{TargetFrameworkDirectory}" olarak ayarlanır.

- COM başvuruları:

   Proje sistemi, `ResolveCOMReferences`iyi bilinen ada sahip bir hedef çağırır. Bu hedef, `ComReferenceWrappers`öğe türü adına sahip öğeler üretmelidir. Bu öğelerin her biri, COM başvurusu için birlikte çalışabilirlik derlemesine giden tam yolu içeren bir öğe belirtimine sahip olmalıdır. Öğelerin, ' ın çıkış klasörüne kopyalanıp kopyalanmayacağını belirten `CopyLocal`adlı yeni meta verilere ek olarak, bu öğelerin içinden geçirilen giriş öğelerinden tüm meta verileri olmalıdır.

- Yerel başvurular

   Proje sistemi, `ResolveNativeReferences`iyi bilinen ada sahip bir hedef çağırır. Bu hedef, `NativeReferenceFile`öğe türü adına sahip öğeler üretmelidir. Öğelerin, başvurunun özgün öğe belirtimini içeren `OriginalItemSpec`adlı yeni bir meta veri parçasına ek olarak, geçirilen giriş öğelerinden tüm meta verilere sahip olması gerekir.

## <a name="performance-shortcuts"></a>Performans kısayolları

 Hata ayıklamayı başlatmak için Visual Studio IDE 'yi kullanırsanız (F5 tuşunu seçerek veya menü çubuğunda Hata **ayıklamayı başlatmak** > **Hata Ayıkla** ' yı seçerek) veya projenizi oluşturmak Için (örneğin, **derleme** > **derleme çözümü**), yapı işlemi performansı artırmak için hızlı bir güncelleştirme denetimi kullanır. Burada özelleştirilmiş yapıların dahili hale gelen dosyalar oluşturma bazı durumlarda, hızlı güncelleştirme kontrolü değiştirilen dosyaları düzgün tanımlamaz. Daha kapsamlı güncelleştirme denetimleri gerektiren projeler, `DISABLEFASTUPTODATECHECK=1`ortam değişkenini ayarlayarak hızlı denetlemeyi kapatabilir. Alternatif olarak, proje bu projeye ya da projenin içe aktardığı bir dosya bir MSBuild özelliği olarak ayarlayabilirsiniz.

 Visual Studio'daki normal yapılarda, hızlı güncelleştirme denetimleri geçerli değildir ve bir komut isteminde derlemenin çağırdığınız gibi Proje derlenir.

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
