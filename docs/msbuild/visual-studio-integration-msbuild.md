---
title: Visual Studio Tümleştirmesi (MSBuild)
titleSuffix: ''
description: farklı araçlar tarafından yazılmış ve özelleştirilmiş derleme işlemlerine sahip olsalar bile Visual Studio projeleri MSBuild biçimde nasıl barındırabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/20/2021
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f38f26bba5311f8077f537edc318f4885cf895ce
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350956"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio tümleştirmesi (MSBuild)

Visual Studio, yönetilen projeleri yüklemek ve derlemek için MSBuild barındırır. MSBuild projeden sorumlu olduğundan, proje farklı bir araç tarafından yazılmış ve özelleştirilmiş bir yapı işlemine sahip olsa bile, MSBuild biçimindeki neredeyse tüm projeler Visual Studio başarılı bir şekilde kullanılabilir.

bu makalede, Visual Studio yüklemek ve derlemek istediğiniz projeleri ve *. targets* dosyalarını özelleştirirken göz önünde bulundurmanız gereken Visual Studio MSBuild barındırmanın belirli yönleri açıklanmaktadır. bunlar, ıntellisense ve hata ayıklama gibi özelliklerin özel projeniz için çalışması için Visual Studio emin olmanıza yardımcı olur.

C++ projeleri hakkında daha fazla bilgi için bkz. [Project dosyaları](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Project dosya adı uzantıları

*MSBuild.exe* , düzeniyle eşleşen herhangi bir proje dosya adı uzantısını tanır *. \* PROJ*. ancak Visual Studio, bu proje dosya adı uzantılarının yalnızca projeyi yükleyecek dile özgü proje sistemini belirleyen bir alt kümesini tanır. Visual Studio, dilden bağımsız MSBuild tabanlı proje sistemine sahip değildir.

örneğin, C# proje sistemi *. csproj* dosyalarını yükler, ancak Visual Studio *. xxproj* dosyasını yükleyemez. rastgele bir dildeki kaynak dosyaları için bir proje dosyası, Visual Studio yüklenecek Visual Basic veya C# proje dosyaları ile aynı uzantıyı kullanmalıdır.

## <a name="well-known-target-names"></a>İyi bilinen hedef adları

 Visual Studio içindeki **Build** komutuna tıkladığınızda projede varsayılan hedef yürütülür. Genellikle, bu hedef de olarak adlandırılır `Build` . **Yeniden oluşturma** veya **Temizleme** komutunun seçilmesi, projede aynı ada sahip bir hedefi yürütmeye çalışır. **Yayımla** ' ya tıkladığınızda projede adlı bir hedef yürütülür `PublishOnly` .

## <a name="configurations-and-platforms"></a>Yapılandırma ve platformlar

 yapılandırmaların, öznitelik içeren bir öğede gruplanmış özellikler tarafından MSBuild projelerinde temsil edilir `PropertyGroup` `Condition` . Visual Studio, görüntülenecek proje yapılandırmalarının ve platformların bir listesini oluşturmak için bu koşullara bakar. Bu listeyi başarıyla ayıklamak için, koşulların aşağıdakine benzer bir biçimi olmalıdır:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio,,, `PropertyGroup` `ItemGroup` `Import` özellik ve öğe öğelerinin bu amaçla bulunduğu koşullara bakar.

## <a name="additional-build-actions"></a>Ek derleme eylemleri

 Visual Studio, **dosya özellikleri** penceresinin **Build Action** özelliği ile bir projedeki bir dosyanın öğe türü adını değiştirmenize izin verir. **Derleme**, **EmbeddedResource**, **içerik** ve **none** öğe türü adları her zaman projenizde olan diğer öğe türü adlarıyla birlikte bu menüde listelenir. Bu menüde her zaman özel öğe türü adlarının kullanılabilir olduğundan emin olmak için adları adlı bir öğe türüne ekleyebilirsiniz `AvailableItemName` . örneğin, proje dosyanıza aşağıdakileri eklemek, içeri aktarılan tüm projeler için **JScript** özel türünü bu menüye ekler:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

Öğe türüne öğe türü adları eklemek, `AvailableItemName` Bu türdeki öğelerin **Çözüm Gezgini** görünmesine neden olur.

> [!NOTE]
> bazı öğe türü adları Visual Studio için özeldir, ancak bu açılan listede listelenmez.

## <a name="in-process-compilers"></a>İşlem içi derleyiciler

 mümkün olduğunda Visual Studio, daha yüksek performans için Visual Basic derleyicisinin işlem içi sürümünü kullanmaya çalışacaktır. (C# için geçerli değildir.) Bunun düzgün çalışması için aşağıdaki koşulların karşılanması gerekir:

- projenin bir hedefinde, Visual Basic projeleri için adlı bir görev olmalıdır `Vbc` .

- `UseHostCompilerIfAvailable`Görevin parametresi true olarak ayarlanmalıdır.

## <a name="design-time-intellisense"></a>Tasarım zamanı IntelliSense

 bir derleme bir çıkış derlemesi oluşturmadan önce Visual Studio ıntellisense desteğini almak için aşağıdaki koşulların karşılanması gerekir:

- Adında bir hedef olması gerekir `Compile` .

- `Compile`Hedefi veya bağımlılıklarından biri, proje için ya da gibi derleyici görevini çağırmalıdır `Csc` `Vbc` .

- `Compile`Hedefi veya bağımlılıklarından biri, derleyicinin IntelliSense için gereken tüm parametreleri, özellikle de tüm başvuruları almasına neden olmalıdır.

- [Işlem içi derleyiciler](#in-process-compilers) bölümünde listelenen koşullar sağlanmalıdır.

## <a name="build-solutions"></a>Çözüm oluşturma

 Visual Studio içinde, çözüm dosyası ve proje derleme sıralaması Visual Studio kendisi tarafından denetlenir. komut satırında *msbuild.exe* bir çözüm oluştururken, MSBuild çözüm dosyasını ayrıştırır ve proje yapılarını sıralar. Her iki durumda da, projeler bağımlılık sırasında tek tek oluşturulmuştur ve proje başvurularına proje başvurularına verilmez. Buna karşılık, tek tek projeler *msbuild.exe* ile oluşturulduğunda proje başvurularına proje başvurularına çapraz yapılır.

 Visual Studio içinde derlerken, özelliği `$(BuildingInsideVisualStudio)` olarak ayarlanır `true` . Bu, projede veya *. targets* dosyalarında, derleme 'in farklı davranmasına neden olacak şekilde kullanılabilir.

## <a name="display-properties-and-items"></a>Özellikleri ve öğeleri görüntüle

 Visual Studio belirli özellik adlarını ve değerleri tanır. örneğin, bir projedeki aşağıdaki özellik **Windows uygulamasının** **Project tasarımcısında** **uygulama türü** kutusunda görünmesine neden olur.

```xml
<OutputType>WinExe</OutputType>
```

 özellik değeri **Project tasarımcısında** düzenlenebilir ve proje dosyasına kaydedilebilir. bu tür bir özelliğe el ile düzenleyerek geçersiz bir değer verilirse Visual Studio, proje yüklendiğinde bir uyarı gösterir ve geçersiz değeri varsayılan bir değerle değiştirir.

 Visual Studio bazı özellikler için varsayılanları anlamıştır. Bu özellikler, varsayılan olmayan değerlere sahip olmadıkları takdirde proje dosyasında kalıcı olmayacaktır.

 Rastgele adlara sahip özellikler Visual Studio gösterilmez. Visual Studio rastgele özellikleri değiştirmek için, proje dosyasını XML düzenleyicisinde açmanız ve onları el ile düzenlemeniz gerekir. daha fazla bilgi için bu konunun ilerleyen bölümlerindeki [Visual Studio proje dosyalarını düzenle](#edit-project-files-in-visual-studio) bölümüne bakın.

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

 görüntülenecek özellik değerlerini belirlerken, yapılandırma bağımlı Visual Studio özellikler yapılandırmayı birbirinden bağımsız olarak kabul eden özelliklerden farklı şekilde değerlendirilir. yapılandırmaya bağımlı olduğunu düşündüğü özellikler için Visual Studio, `Configuration` ve `Platform` özelliklerini uygun şekilde ayarlar ve MSBuild projeyi yeniden değerlendirmesini sağlar. Yapılandırmayı bağımsız olarak kabul eden özellikler için, koşulların nasıl değerlendirileceğini belirsiz hale gelir.

 Öğelerin **Çözüm Gezgini** gösterilip gösterilmeyeceğine karar vermek amacıyla öğelerdeki Koşullu ifadeler her zaman göz ardı edilir.

## <a name="debugging"></a>Hata Ayıklama

 çıkış derlemesini bulup başlatmak ve hata ayıklayıcıyı iliştirmek için, Visual Studio özellikler `OutputPath` , `AssemblyName` ve `OutputType` doğru şekilde tanımlanması gerekir. Derleme işlemi derleyicinin bir *. pdb* dosyası oluşturmasına neden değilse, hata ayıklayıcısı iliştirilemiyor.

## <a name="design-time-target-execution"></a>Tasarım zamanı hedef yürütme

 Visual Studio, bir projeyi yüklediğinde belirli adlarla hedefleri yürütmeye çalışır. Bu hedefler,,, `Compile` `ResolveAssemblyReferences` ve içerir `ResolveCOMReferences` `GetFrameworkPaths` `CopyRunEnvironmentFiles` . Visual Studio bu hedefleri çalıştırarak derleyicinin ıntellisense sağlamak üzere başlatılabilmesini, hata ayıklayıcının başlatılabilir olduğunu ve Çözüm Gezgini görüntülenen başvuruların çözümlenebilmesini sağlar. bu hedefler yoksa, proje doğru şekilde yüklenir ve oluşturulur, ancak Visual Studio tasarım zamanı deneyimi tam olarak işlevsel olmayacaktır.

## <a name="edit-project-files-in-visual-studio"></a>Visual Studio proje dosyalarını Düzenle

 bir MSBuild projesini doğrudan düzenlemek için, proje dosyasını Visual Studio XML düzenleyicisinde açabilirsiniz.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için

1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Project kaldır**' ı seçin.

     Proje işaretlendi **(kullanılamıyor)**.

2. **Çözüm Gezgini**' de, kullanılamayan proje için kısayol menüsünü açın ve ardından **Düzenle \<Project File>**' yi seçin.

     proje dosyası Visual Studio XML düzenleyicisinde açılır.

3. Proje dosyasını düzenleyin, kaydedin ve ardından kapatın.

4. **Çözüm Gezgini**' de, kullanılamayan proje için kısayol menüsünü açın ve ardından **Project yeniden yükle**' yi seçin.

## <a name="intellisense-and-validation"></a>IntelliSense ve doğrulama

 proje dosyalarını düzenlemek için XML düzenleyicisini kullanırken, ıntellisense ve doğrulama MSBuild şema dosyaları tarafından çalıştırılır. Bunlar, *\<Visual Studio installation directory> \Xml\schemas\10&\ MSBuild* içinde bulunan şema önbelleğine yüklenir.

 temel MSBuild türleri microsoft *. build. core. xsd* ve Visual Studio tarafından kullanılan ortak türlerde tanımlanmıştır, *microsoft. build. commontypes. xsd* dosyasında tanımlanmıştır. Şemaları, özel öğe türü adları, özellikleri ve görevleri için IntelliSense ve doğrulamaya sahip olacak şekilde özelleştirmek için *Microsoft. Build. xsd*' yi düzenleyebilir ya da CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Kendi şemanızı oluşturursanız, **Özellikler** penceresini kullanarak bulmak için XML düzenleyicisini yönlendirirsiniz.

## <a name="edit-loaded-project-files"></a>Yüklenen proje dosyalarını Düzenle

 Visual Studio proje dosyaları ve proje dosyaları tarafından içeri aktarılan dosyaların içeriğini önbelleğe alır. yüklenmiş bir proje dosyasını düzenlerseniz, değişikliklerin etkili olması için Visual Studio otomatik olarak projeyi yeniden yüklemenizi ister. Ancak, yüklenen bir proje tarafından içeri aktarılan bir dosyayı düzenlerseniz, yeniden yükleme istemi olmaz ve değişikliklerin etkili olması için projeyi el ile kaldırıp yeniden yüklemeniz gerekir.

## <a name="output-groups"></a>Çıkış grupları

 *Microsoft.Common.targets içinde tanımlanan birkaç hedefin* veya ile biten adları `OutputGroups` `OutputGroupDependencies` vardır. Visual Studio belirli proje çıkışlarının listelerini almak için bu hedefleri çağırıyor. Örneğin hedef, `SatelliteDllsProjectOutputGroup` bir derlemenin oluşturacakları tüm uydu derlemelerinin listesini oluşturur. Bu çıkış grupları yayımlama, dağıtım ve projeden projeye başvurular gibi özellikler tarafından kullanılır. Bunları tanımlamadan projeler, Visual Studio'de yük Visual Studio ancak bazı özellikler düzgün çalışmayabilir.

## <a name="reference-resolution"></a>Başvuru çözümlemesi

 Başvuru çözümlemesi, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. Visual Studio penceresinde her başvuru için ayrıntılı özellikleri göstermek için başvuru çözümlemesi **tetiklenin.** Aşağıdaki listede üç başvuru türü ve bunların nasıl çözümlenleri açıkmektedir.

- Derleme başvuruları:

   Proje sistemi, iyi bilinen adıyla bir hedef `ResolveAssemblyReferences` arar. Bu hedef, öğe türü adıyla öğeler `ReferencePath` üretmeli. Bu öğelerin her biri, başvuru yolunun tamamını içeren bir öğe belirtimi `Include` (bir öğenin özniteliğinin değeri) içerir. Öğeler, aşağıdaki yeni meta verilere ek olarak giriş öğelerinden geçirilen tüm meta verileri içerir:

  - `CopyLocal`, derlemenin çıkış klasörüne kopyalanmış olup olmadığını belirtir, true veya false olarak ayarlanır.

  - `OriginalItemSpec`, başvuru için özgün öğe belirtimlerini içerir.

  - `ResolvedFrom`, dizinden çözümlendiyse "{TargetFrameworkDirectory}" .NET Framework ayarlayın.

- COM başvuruları:

   Proje sistemi, iyi bilinen adıyla bir hedef `ResolveCOMReferences` arar. Bu hedef, öğe türü adıyla öğeler `ComReferenceWrappers` üretmeli. Bu öğelerin her biri, COM başvurusu için birlikte çalışma derlemesi yolunun tamamını içeren bir öğe belirtimlerine sahip olması gerekir. Öğelerin, derlemenin çıkış klasörüne kopyalanır mı, true mu yoksa false olarak ayar mı olacağını belirten yeni meta verilere ek olarak, giriş öğelerinden geçirilen tüm meta verilere sahip olması `CopyLocal` gerekir.

- Yerel başvurular

   Proje sistemi, iyi bilinen adıyla bir hedef `ResolveNativeReferences` arar. Bu hedef, öğe türü adıyla öğeler `NativeReferenceFile` üretmeli. Öğeler, başvurunun özgün öğe belirtimlerini içeren adlı yeni bir meta veri parçasına ek olarak, giriş öğelerinden geçirilen tüm `OriginalItemSpec` meta verileri içerir.

## <a name="performance-shortcuts"></a>Performans kısayolları

 Hata ayıklamaya başlamak için Visual Studio IDE'yi kullanırsanız (F5 anahtarını seçerek veya menü çubuğunda Hata Ayıklamayı Başlat'ı seçerek) veya projenizi derlemek (derleme çözümü gibi), derleme işlemi performansı geliştirmek için hızlı bir güncelleştirme denetimi  >     >  kullanır. Özelleştirilmiş derlemelerin sırasıyla dosya oluşturması durumlarında hızlı güncelleştirme denetimi değiştirilen dosyaları doğru şekilde tanımlamaz. Daha kapsamlı güncelleştirme denetimlerine ihtiyaç olan projeler, ortam değişkenlerini ayarerek hızlı denetimi devre dışı `DISABLEFASTUPTODATECHECK=1` bırakır. Alternatif olarak, projeler bunu projede bir MSBuild veya projenin içeri aktaran bir dosyada bir dosya olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Visual Studio: Visual Studio genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [IDE'den derleme başlatma](../msbuild/starting-a-build-from-within-the-ide.md)
- [Dosyanın uzantılarını .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
- [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)