---
title: Visual Studio Tümleştirmesi (MSBuild)
titleSuffix: ''
description: Farklı Visual Studio ve özelleştirilmiş derleme işlemlerine sahip olsalar MSBuild bir biçimde nasıl barındıracaklarını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 8c2ea012fecdc5d97c69da09969d0c29b4b93503
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970509"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio tümleştirmesi (MSBuild)

Visual Studio projeleri MSBuild derlemek için konakları barındıracak. MSBuild projeden sorumlu olduğundan, proje farklı bir araç tarafından yazılsa ve özelleştirilmiş bir derleme işlemi olsa bile MSBuild biçimindeki neredeyse tüm proje Visual Studio'de başarıyla kullanılabilir.

 Bu makalede, Visual Studio'nin MSBuild ve *.targets* dosyaları özelleştirilebilirken dikkate alınacak belirli özellikleri açık Visual Studio. Bunlar IntelliSense ve hata ayıklama Visual Studio özel projeniz için çalışmanızı sağlar.

 C++ projeleri hakkında bilgi için [bkz. Project dosyaları.](/cpp/build/reference/project-files)

## <a name="project-file-name-extensions"></a>Project adı uzantıları

 *MSBuild.exe* desenle eşleşen tüm proje dosya adı uzantılarını *tanır. \* proj*. Ancak Visual Studio, projeyi yükecek dile özgü proje sistemini belirleyen bu proje dosya adı uzantılarının yalnızca bir alt kümesini tanır. Visual Studio, dilden bağımsız bir MSBuild tabanlı proje sistemine sahip değildir.

 Örneğin, C# proje sistemi *.csproj* dosyalarını yükler, Visual Studio *bir .xxproj dosyası yükleyemedi.* Rastgele bir dil içinde kaynak dosyalar için bir proje dosyası, Visual Basic C# proje dosyalarının Visual Studio.

## <a name="well-known-target-names"></a>İyi bilinen hedef adları

 Visual Studio'da Derleme komutuna tıklar, projede varsayılan hedefi yürütür.  Bu hedef genellikle olarak da adlandırılmış `Build` olur. Yeniden Oluştur **veya** **Temizle** komutu seçerek projede aynı adı alan bir hedef yürütmeye çalışabilirsiniz. **Yayımla'ya** tıklar, projede `PublishOnly` adlı bir hedef yürütür.

## <a name="configurations-and-platforms"></a>Yapılandırmalar ve platformlar

 Yapılandırmalar, MSBuild içeren bir öğede gruplara göre `PropertyGroup` farklı projelerde `Condition` temsil eder. Visual Studio proje yapılandırmalarının ve platformlarının bir listesini oluşturmak için bu koşulların nasıl olduğunu gösterir. Bu listeyi başarıyla ayıklamak için koşulların aşağıdakine benzer bir biçimi olmalıdır:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio için , , `PropertyGroup` `ItemGroup` , `Import` özelliği ve öğe öğelerinde koşullarına bakabilirsiniz.

## <a name="additional-build-actions"></a>Ek derleme eylemleri

 Visual Studio projesinde dosyanın öğe türü adını Dosya özellikleri penceresinin **Derleme Eylemi** özelliğiyle **değiştirmenizi** sağlar. **Derleme,** **EmbeddedResource,** **İçerik** ve Hiçbiri öğe türü adları her zaman bu menüde ve projeniz içinde zaten bulunan diğer öğe türü adlarına ek olarak listelenir.  Özel öğe türü adlarının bu menüde her zaman kullanılabilir olmasını sağlamak için adları adlı bir öğe türüne `AvailableItemName` ekleyebilirsiniz. Örneğin, proje dosyanıza aşağıdakiler ekleyen özel tür **JScript** içeri aktaran tüm projeler için bu menüye özel türü ekler:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

Öğe türüne öğe türü `AvailableItemName` adları eklemek, bu türdeki öğelerin öğesinde Çözüm Gezgini.

> [!NOTE]
> Bazı öğe türü adları bu Visual Studio için özeldir ancak bu açılan listede listelenmiyor.

## <a name="in-process-compilers"></a>İşlem içinde derleyiciler

 Mümkün olduğunda Visual Studio performansın artması için Visual Basic derlemenin işlem içinde sürümünü kullanmayı denemeniz gerekir. (C# için geçerli değildir.) Bunun düzgün çalışması için aşağıdaki koşulların karşı olması gerekir:

- Projenin hedeflerinde, proje için adlandırılmış bir görev `Vbc` Visual Basic gerekir.

- `UseHostCompilerIfAvailable`Görevin parametresi true olarak ayar olmalıdır.

## <a name="design-time-intellisense"></a>Tasarım zamanı IntelliSense

 Derleme bir çıkış derlemesi oluşturmadan Visual Studio içinde IntelliSense desteği almak için aşağıdaki koşulların karşılan olması gerekir:

- adlı bir hedef olması `Compile` gerekir.

- Hedef `Compile` veya bağımlılıklarından biri, veya gibi proje için derleyici görevini `Csc` çağırarak. `Vbc`

- Hedef veya bağımlılıklarından biri, derleyicinin IntelliSense için gerekli tüm parametreleri, özellikle de tüm başvuruları `Compile` almalarına neden olmalıdır.

- İşlem içinde [derleyiciler bölümünde listelenen koşulların](#in-process-compilers) karşılan olması gerekir.

## <a name="build-solutions"></a>Çözüm oluşturma

 Bu Visual Studio çözüm dosyası ve proje derlemesi kendi kendine Visual Studio denetlenmektedir. Komut satırına *msbuild.exe* bir çözüm MSBuild çözüm dosyasını ayrıştırır ve projenin derlemesini siparişler. Her iki durumda da projeler bağımlılık sırasına göre ayrı ayrı, projeden projeye başvurular ise çapraz geçiş olmaz. Buna karşılık, tek tek projelermsbuild.exe *projeden* projeye başvurular çapraz geçiştir.

 İç Visual Studio özelliği `$(BuildingInsideVisualStudio)` olarak `true` ayarlanır. Bu, derlemenin farklı davranmasına neden olmak için proje veya *.targets* dosyalarında kullanılabilir.

## <a name="display-properties-and-items"></a>Özellikleri ve öğeleri görüntüleme

 Visual Studio özellik adlarını ve değerlerini tanır. Örneğin, bir projede aşağıdaki özellik, **Windows Application'ın** Project  Tasarımcısı'nda Uygulama Türü **kutusunda görünmesine neden olur.**

```xml
<OutputType>WinExe</OutputType>
```

 Özellik değeri, Project **Designer'da düzenlenebilir** ve proje dosyasına kaydedilebilir. Böyle bir özele el ile düzenleme ile geçersiz bir değer verilirse, Visual Studio proje yüklendiğinde bir uyarı gösterir ve geçersiz değeri varsayılan değerle değiştirir.

 Visual Studio özelliklerin varsayılanlarını anlar. Bu özellikler varsayılan olmayan değerlere sahip olmadığı sürece proje dosyasında kalıcı olmaz.

 Rastgele adlara sahip özellikler, Visual Studio. Bu dosyada rastgele Visual Studio değiştirmek için proje dosyasını XML düzenleyicisinde açıp el ile düzenlemeniz gerekir. Daha fazla bilgi için bu [konunun devam Visual Studio](#edit-project-files-in-visual-studio) Proje dosyalarını düzenleme bölümüne bakın.

 Projede rastgele öğe türü adlarıyla tanımlanan öğeler varsayılan olarak proje düğümlerinin **Çözüm Gezgini** öğesinde görüntülenir. Bir öğeyi görüntüden gizlemek için meta verileri `Visible` olarak `false` ayarlayın. Örneğin, aşağıdaki öğe derleme sürecine katılacak ancak öğesinde **Çözüm Gezgini.**

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> `Visible`Meta veriler C++ projeleri **Çözüm Gezgini** tarafından yoksayılır. Öğeler false olarak ayarlansa `Visible` bile her zaman gösterilir.

 Projeye aktarılan dosyalarda bildirilen öğeler varsayılan olarak görüntülenmez. Derleme işlemi sırasında oluşturulan öğeler hiçbir zaman içinde **Çözüm Gezgini.**

## <a name="conditions-on-items-and-properties"></a>Öğeler ve özelliklerle ilgili koşullar

 Derleme sırasında tüm koşullar tam olarak kabul edildi.

 Görüntülenecek özellik değerlerini belirlerken, yapılandırmaya bağımlı Visual Studio dikkate alan özellikler, yapılandırmadan bağımsız olarak değerlendirilen özelliklerden farklı değerlendirilir. Yapılandırmaya bağımlı olarak kabul Visual Studio özellikleri uygun şekilde ayarlar ve MSBuild yeniden `Configuration` `Platform` değerlendirmesini sağlar. Yapılandırmadan bağımsız olarak değerlendiren özellikler için koşulların nasıl değerlendirileceğini belirsizdir.

 Öğelerdeki koşullu ifadeler, öğenin öğesinde görüntülendiğinden karar verme amacıyla her zaman **yoksayılır** Çözüm Gezgini.

## <a name="debugging"></a>Hata Ayıklama

 Çıkış derlemeyi bulup başlatmak ve hata ayıklayıcıyı eklemek için, Visual Studio , ve doğru şekilde `OutputPath` `AssemblyName` `OutputType` tanımlanmalıdır. Derleme işlemi derleyicinin bir *.pdb* dosyası oluşturmasını neden oluşturmazsa hata ayıklayıcı ekleyemez.

## <a name="design-time-target-execution"></a>Tasarım zamanı hedef yürütme

 Visual Studio projeyi yüklerken belirli adlarla hedefleri yürütmeye çalışır. Bu hedefler arasında `Compile` , , , ve yer `ResolveAssemblyReferences` `ResolveCOMReferences` `GetFrameworkPaths` `CopyRunEnvironmentFiles` almaktadır. Visual Studio bu hedefleri çalıştırarak derleyicinin IntelliSense sağlamak için başlatılana, hata ayıklayıcı başlatılana ve bu hedeflerde görüntülenen Çözüm Gezgini çözümlenebilirsiniz. Bu hedefler yoksa proje doğru şekilde yük binecek ve derlemesini tamamlar, ancak Visual Studio tasarım zamanı deneyimi tam olarak işlevsel olmayacaktır.

## <a name="edit-project-files-in-visual-studio"></a>Proje dosyalarını Visual Studio

 Bir MSBuild doğrudan düzenlemek için proje dosyasını xml düzenleyicisinde Visual Studio açabilirsiniz.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için

1. Bu **Çözüm Gezgini** proje için kısayol menüsünü açın ve Sonra Yüklemeden kaldır'ı **Project.**

     Proje işaretlenmiş **(kullanılamıyor)**.

2. Bu **Çözüm Gezgini,** kullanılamayan projenin kısayol menüsünü açın ve düzenle'yi **seçin. \<Project File>**

     Proje dosyası xml düzenleyicisinde Visual Studio açılır.

3. Proje dosyasını düzenleyin, kaydedin ve kapatın.

4. Bu **Çözüm Gezgini,** kullanılamayan projenin kısayol menüsünü açın ve ardından Yeniden Yükle'yi **Project.**

## <a name="intellisense-and-validation"></a>IntelliSense ve doğrulama

 Proje dosyalarını düzenlemek için XML düzenleyicisi kullanılırken IntelliSense ve doğrulama, xml MSBuild tarafından çalıştırılır. Bunlar \ *\<Visual Studio installation directory> Xml\Schemas\1033\MSBuild* konumunda bulunan şema önbelleğine yüklenir.

 Temel MSBuild türleri *Microsoft.Build.Core.xsd* içinde tanımlanır ve Visual Studio yaygın türler *Microsoft.Build.CommonTypes.xsd* içinde tanımlanır. Şemaları özel öğe türü adları, özellikleri ve görevleri için IntelliSense ve doğrulamaya sahip olacak şekilde özelleştirmek için *Microsoft.Build.xsd'yi* düzenleyebilir veya CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Kendi şemanızı oluşturmanız, XML düzenleyicisini Özellikler penceresini kullanarak bulması için **yönlendirebilirsiniz.**

## <a name="edit-loaded-project-files"></a>Yüklenen proje dosyalarını düzenleme

 Visual Studio, proje dosyaları tarafından içe aktarılan proje dosyalarının ve dosyaların içeriğini önbelleğe alınır. Yüklenen bir proje dosyasını düzenlersiniz, Visual Studio değişikliklerin etkili olmak için projeyi yeniden yüklemenizi otomatik olarak istenir. Ancak yüklenen bir proje tarafından içe aktarılan bir dosyayı düzenlersiniz, yeniden yükleme istemi olmaz ve değişikliklerin etkili olması için projeyi el ile kaldırmanız ve yeniden yüklemeniz gerekir.

## <a name="output-groups"></a>Çıkış grupları

 *Microsoft. Common. targets* içinde tanımlanan birçok hedef, veya ile biten adlara sahiptir `OutputGroups` `OutputGroupDependencies` . Visual Studio, proje çıkışları için belirli listeleri almak üzere bu hedefleri çağırır. Örneğin, hedef, `SatelliteDllsProjectOutputGroup` derleme oluşturulacak tüm uydu derlemelerinin listesini oluşturur. Bu çıktı grupları, proje başvurularına yayımlama, dağıtım ve proje gibi özellikler tarafından kullanılır. onları tanımlamayan projeler Visual Studio yüklenir ve oluşturulur, ancak bazı özellikler düzgün çalışmayabilir.

## <a name="reference-resolution"></a>Başvuru çözümleme

 Başvuru çözümleme, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. Visual Studio, **özellikler** penceresindeki her bir başvurunun ayrıntılı özelliklerini göstermek için başvuru çözümlemesini tetiklemelidir. Aşağıdaki listede, üç tür başvuru ve nasıl çözümlendikleri açıklanmaktadır.

- Bütünleştirilmiş kod başvuruları:

   Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveAssemblyReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `ReferencePath` . Bu öğelerin her biri, `Include` başvurunun tam yolunu içeren bir öğe belirtimine (bir öğenin özniteliğinin değeri) sahip olmalıdır. Öğelerin, aşağıdaki yeni meta verilere ek olarak, geçirilen giriş öğelerinden tüm meta verilere sahip olması gerekir:

  - `CopyLocal`, derlemenin çıkış klasörüne kopyalanıp kopyalanmayacağını belirtir, true veya false olarak ayarlayın.

  - `OriginalItemSpec`, başvurunun orijinal öğe belirtimini içeren.

  - `ResolvedFrom`, .NET Framework dizininden çözümlenmişse "{targetframeworkdirectory}" olarak ayarlanır.

- COM başvuruları:

   Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveCOMReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `ComReferenceWrappers` . Bu öğelerin her biri, COM başvurusunun birlikte çalışma derlemesine tam yolu içeren bir öğe belirtimine sahip olmalıdır. Öğelerin, aynı ada sahip yeni meta verilere ek olarak,, `CopyLocal` derlemenin çıkış klasörüne kopyalanıp kopyalanmayacağını belirten, true veya false olarak ayarlandığını belirten, içindeki giriş öğelerinden tüm meta verileri olmalıdır.

- Yerel başvurular

   Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveNativeReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `NativeReferenceFile` . Öğelerin, `OriginalItemSpec` başvurunun orijinal öğe belirtimini içeren, adlı yeni bir meta veri parçasına ek olarak, geçirilen giriş öğelerinden tüm meta verilere sahip olması gerekir.

## <a name="performance-shortcuts"></a>Performans kısayolları

 hata ayıklamayı başlatmak için Visual Studio ıde kullanıyorsanız (F5 tuşunu seçerek veya menü çubuğunda **hata**  >  **ayıklamayı başlat** ' ı seçerek) veya projenizi oluşturmak için (örneğin, **derleme**  >  **çözümü**), yapı işlemi performansı artırmak için hızlı bir güncelleştirme denetimi kullanır. Özelleştirilmiş yapıların, yerleşik olarak oluşturulan dosyalar oluşturmasındaki bazı durumlarda, hızlı güncelleştirme denetimi değiştirilen dosyaları doğru şekilde tanımlamaz. Daha kapsamlı güncelleştirme denetimleri gerektiren projeler, ortam değişkenini ayarlayarak hızlı denetlemeyi kapatabilir `DISABLEFASTUPTODATECHECK=1` . alternatif olarak, projeler bunu projede veya proje içeri aktardığı bir dosyada MSBuild özelliği olarak ayarlayabilir.

 Visual Studio düzenli derlemeler için hızlı güncelleştirme denetimi uygulanmaz ve proje, derlemeyi bir komut isteminde çağırırı olarak derler.

## <a name="see-also"></a>Ayrıca bkz.

- [nasıl yapılır: Visual Studio derleme işlemini genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [IDE içinden derleme başlatma](../msbuild/starting-a-build-from-within-the-ide.md)
- [.NET Framework uzantılarını Kaydet](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
