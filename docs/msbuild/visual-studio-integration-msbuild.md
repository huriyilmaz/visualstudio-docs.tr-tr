---
title: Visual Studio Tümleştirmesi (MSBuild)
titleSuffix: ''
description: Farklı Visual Studio ve özelleştirilmiş derleme işlemlerine sahip olsalar bile, projeleri MSBuild biçiminde nasıl barındıracaklarını öğrenin.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63e78d935d515ccafda461a8f7af77623387940b
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602156"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio tümleştirmesi (MSBuild)

Visual Studio projeleri yüklemek ve derlemek için MSBuild'i barındıracak. MSBuild projeden sorumlu olduğundan, proje farklı bir araç tarafından yazılsa ve özelleştirilmiş bir derleme işlemi olsa bile, MSBuild biçimindeki neredeyse tüm proje Visual Studio'de başarıyla kullanılabilir.

 Bu makalede, Visual Studio'nin MSBuild barındırması ile ilgili, proje ve *.targets* dosyaları özelleştirilebilirken dikkate alınacak belirli yönleri açık Visual Studio. Bunlar, IntelliSense gibi Visual Studio ve hata ayıklama özelliklerinin özel projenize uygun olduğundan emin olur.

 C++ projeleri hakkında bilgi için bkz. [Proje dosyaları.](/cpp/build/reference/project-files)

## <a name="project-file-name-extensions"></a>Proje dosya adı uzantıları

 *MSBuild.exe* desenle eşleşen tüm proje dosya adı uzantılarını *tanır. \* proj*. Ancak Visual Studio, projeyi yükecek dile özgü proje sistemini belirleyen bu proje dosya adı uzantılarının yalnızca bir alt kümesini tanır. Visual Studio, dilden bağımsız MSBuild tabanlı bir proje sistemine sahip değildir.

 Örneğin, C# proje sistemi *.csproj* dosyalarını yükler, Visual Studio *bir .xxproj dosyası yükleyemedi.* Rastgele bir dil içinde kaynak dosyalar için bir proje dosyası, Visual Basic veya C# proje dosyalarının Visual Studio.

## <a name="well-known-target-names"></a>İyi bilinen hedef adları

 Visual Studio'da Derleme komutuna tıklar, projede varsayılan hedefi yürütür.  Bu hedef genellikle olarak da adlandırılmış `Build` olur. Yeniden Oluştur **veya** **Temizle** komutu seçerek projede aynı adı alan bir hedef yürütmeye çalışabilirsiniz. **Yayımla'ya** tıklar, projede `PublishOnly` adlı bir hedef yürütür.

## <a name="configurations-and-platforms"></a>Yapılandırmalar ve platformlar

 Yapılandırmalar, MSBuild projelerinde öznitelik içeren bir öğede `PropertyGroup` grup edilen özelliklere göre `Condition` temsil eder. Visual Studio proje yapılandırmalarının ve platformlarının bir listesini oluşturmak için bu koşulların nasıl göründüğünü gösterir. Bu listeyi başarıyla ayıklamak için koşulların aşağıdakine benzer bir biçimi olmalıdır:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio için `PropertyGroup` , , , `ItemGroup` özelliği ve `Import` öğe öğelerinde koşullarına bakabilirsiniz.

## <a name="additional-build-actions"></a>Ek derleme eylemleri

 Visual Studio projesinde dosyanın öğe türü adını Dosya özellikleri penceresinin **Derleme Eylemi** özelliğiyle **değiştirmenizi** sağlar. **Derleme,** **EmbeddedResource,** **İçerik** ve Hiçbiri öğe türü adları her zaman bu menüde ve projeniz içinde zaten bulunan diğer öğe türü adlarına ek olarak listelenir.  Özel öğe türü adlarının bu menüde her zaman kullanılabilir olmasını sağlamak için adları adlı bir öğe türüne `AvailableItemName` ekleyebilirsiniz. Örneğin, proje dosyanıza aşağıdakini eklemek, içeri aktaran tüm projeler için bu menüye **özel JScript** türünü ekler:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

Öğe türüne öğe türü `AvailableItemName` adları eklemek, bu türdeki öğelerin öğesinde Çözüm Gezgini.

> [!NOTE]
> Bazı öğe türü adları, özel Visual Studio ancak bu açılan listede yer alan adlar değildir.

## <a name="in-process-compilers"></a>İşlem içinde derleyiciler

 Mümkün olduğunda, Visual Studio performansın artması için Visual Basic için Visual Basic sürümünü kullanmaya çalışabilirsiniz. (C# için geçerli değildir.) Bunun doğru çalışması için aşağıdaki koşulların karşı olması gerekir:

- Projenin hedeflerinde, proje için adlandırılmış bir görev `Vbc` Visual Basic gerekir.

- `UseHostCompilerIfAvailable`Görevin parametresi true olarak ayar olmalıdır.

## <a name="design-time-intellisense"></a>Tasarım zamanı IntelliSense

 Derleme bir çıkış derlemesi oluşturmadan önce Visual Studio intelliSense desteği almak için aşağıdaki koşulların karşılan olması gerekir:

- adlı bir hedef olması `Compile` gerekir.

- Hedef `Compile` veya bağımlılıklarından biri, proje için veya gibi derleyici görevini `Csc` çağırarak. `Vbc`

- Hedef veya bağımlılıklarından biri, derleyicinin IntelliSense için gerekli tüm parametreleri, özellikle de tüm başvuruları `Compile` almalarına neden olmalıdır.

- İşlem içinde [derleyiciler bölümünde listelenen koşulların](#in-process-compilers) karşılan olması gerekir.

## <a name="build-solutions"></a>Çözüm oluşturma

 Bu Visual Studio, çözüm dosyası ve proje derleme sıralaması kendi başına Visual Studio denetlenmektedir. Komut satırına *msbuild.exe* çözüm derlemek için MSBuild çözüm dosyasını ayrıştırır ve projenin derlemesini sipariş ediyor. Her iki durumda da projeler bağımlılık sırasına göre ayrı ayrı, projeden projeye başvurular ise çapraz geçiş olmaz. Buna karşılık, tek tek projelermsbuild.exe *projeden* projeye başvurular çapraz geçiştir.

 İç Visual Studio özelliği `$(BuildingInsideVisualStudio)` olarak `true` ayarlanır. Bu, derlemenin farklı davranmasına neden olmak için proje veya *.targets* dosyalarında kullanılabilir.

## <a name="display-properties-and-items"></a>Özellikleri ve öğeleri görüntüleme

 Visual Studio özellik adlarını ve değerlerini tanır. Örneğin, bir projede aşağıdaki özellik **Windows** Uygulaması'nın Proje Tasarımcısı'nda **Uygulama Türü** kutusunda görünmesine **neden olur.**

```xml
<OutputType>WinExe</OutputType>
```

 Özellik değeri Proje Tasarımcısı'nda **düzenlenebilir ve** proje dosyasına kaydedilebilir. Böyle bir özele el ile düzenleme ile geçersiz bir değer verilirse, Visual Studio proje yüklendiğinde bir uyarı gösterir ve geçersiz değeri varsayılan değerle değiştirir.

 Visual Studio bazı özelliklerin varsayılanlarını anlar. Bu özellikler varsayılan olmayan değerlere sahip olmadığı sürece proje dosyasında kalıcı olmaz.

 Rastgele adlara sahip özellikler, Visual Studio. Bu dosyada rastgele Visual Studio değiştirmek için proje dosyasını XML düzenleyicisinde açıp el ile düzenlemeniz gerekir. Daha fazla bilgi için bu konunun [devam Visual Studio](#edit-project-files-in-visual-studio) proje dosyalarını düzenleme bölümüne bakın.

 Projede rastgele öğe türü adlarıyla tanımlanan öğeler varsayılan olarak proje düğümlerinin **Çözüm Gezgini** öğesinde görüntülenir. Bir öğeyi görüntüden gizlemek için meta verileri `Visible` olarak `false` ayarlayın. Örneğin, aşağıdaki öğe derleme sürecine katacak ancak öğesinde **Çözüm Gezgini.**

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Meta `Visible` veriler C++ **projeleri Çözüm Gezgini** tarafından yoksayılır. Öğeler false olarak ayarlansa `Visible` bile her zaman gösterilir.

 Projeye aktarılan dosyalarda bildirilen öğeler varsayılan olarak görüntülenmez. Derleme işlemi sırasında oluşturulan öğeler hiçbir zaman içinde **Çözüm Gezgini.**

## <a name="conditions-on-items-and-properties"></a>Öğeler ve özelliklerle ilgili koşullar

 Derleme sırasında tüm koşullar tam olarak kabul edildi.

 Görüntülenecek özellik değerleri belirlenirken, yapılandırmaya bağımlı Visual Studio dikkate alan özellikler, yapılandırmadan bağımsız olarak değerlendirilen özelliklerden farklı değerlendirilir. Yapılandırmaya bağımlı olarak kabul Visual Studio özellikleri uygun şekilde ayarlar ve `Configuration` `Platform` MSBuild'e projeyi yeniden değerlendirmesini sağlar. Yapılandırmadan bağımsız olarak değerlendiren özellikler için koşulların nasıl değerlendirileceğini belirsizdir.

 Öğelerdeki koşullu ifadeler, öğenin öğesinde görüntülendiğinden karar verme amacıyla her zaman **yoksayılır** Çözüm Gezgini.

## <a name="debugging"></a>Hata Ayıklama

 Çıkış derlemeyi bulup başlatmak ve hata ayıklayıcıyı eklemek için, Visual Studio , ve `OutputPath` `AssemblyName` doğru şekilde `OutputType` tanımlanmalıdır. Derleme işlemi derleyicinin bir *.pdb* dosyası oluşturmasını neden oluşturmazsa hata ayıklayıcı ekleyemez.

## <a name="design-time-target-execution"></a>Tasarım zamanı hedef yürütme

 Visual Studio projeyi yüklerken belirli adlarla hedefleri yürütmeye çalışır. Bu hedefler arasında `Compile` , , , ve yer `ResolveAssemblyReferences` `ResolveCOMReferences` `GetFrameworkPaths` `CopyRunEnvironmentFiles` almaktadır. Visual Studio bu hedefleri çalıştırarak derleyicinin IntelliSense sağlamak için başlatılana, hata ayıklayıcı başlatılana ve bu hedeflerde görüntülenen Çözüm Gezgini çözümlenebilirsiniz. Bu hedefler yoksa proje doğru şekilde yük binecek ve derlemesini tamamlar ancak Visual Studio tasarım zamanı deneyimi tam olarak işlevsel olmayacaktır.

## <a name="edit-project-files-in-visual-studio"></a>Proje dosyalarını Visual Studio

 MsBuild projesini doğrudan düzenlemek için proje dosyasını xml düzenleyicisinde Visual Studio açabilirsiniz.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için

1. Bu **Çözüm Gezgini** proje kısayol menüsünü açın ve Projeyi Kaldır'ı **seçin.**

     Proje işaretlenmiş **(kullanılamıyor)**.

2. Bu **Çözüm Gezgini** kullanılamayan projenin kısayol menüsünü açın ve Düzenle'yi **seçin. \<Project File>**

     Proje dosyası xml düzenleyicisinde Visual Studio açılır.

3. Proje dosyasını düzenleyin, kaydedin ve kapatın.

4. Bu **Çözüm Gezgini** kullanılamayan projenin kısayol menüsünü açın ve Projeyi Yeniden **Yükle'yi seçin.**

## <a name="intellisense-and-validation"></a>IntelliSense ve doğrulama

 Proje dosyalarını düzenlemek için XML düzenleyicisi kullanılırken, IntelliSense ve doğrulama MSBuild şema dosyaları tarafından çalıştırılır. Bunlar\ *\<Visual Studio installation directory> Xml\Schemas\1033\MSBuild* konumunda bulunan şema önbelleğine yüklenir.

 Çekirdek MSBuild türleri *Microsoft.Build.Core.xsd* içinde tanımlanır ve Visual Studio kullanılan yaygın türler *Microsoft.Build.CommonTypes.xsd* içinde tanımlanır. Şemaları özel öğe türü adları, özellikleri ve görevleri için IntelliSense ve doğrulamaya sahip olacak şekilde özelleştirmek için *Microsoft.Build.xsd'yi* düzenleyebilir veya CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Kendi şemanızı oluşturmanız, XML düzenleyicisini Özellikler penceresini kullanarak bulması için **yönlendirebilirsiniz.**

## <a name="edit-loaded-project-files"></a>Yüklenen proje dosyalarını düzenleme

 Visual Studio, proje dosyaları tarafından aktarılan proje dosyalarının ve dosyaların içeriğini önbelleğe alınır. Yüklenen bir proje dosyasını düzenlersiniz, Visual Studio değişikliklerin etkili olmak için projeyi yeniden yüklemenizi otomatik olarak istenir. Ancak, yüklenen bir proje tarafından içe aktarılan bir dosyayı düzenlersiniz, yeniden yükleme istemi olmaz ve değişikliklerin etkili olması için projeyi el ile kaldırmanız ve yeniden yüklemeniz gerekir.

## <a name="output-groups"></a>Çıkış grupları

 *Microsoft.Common.targets içinde tanımlanan birkaç hedefin* veya ile biten adları `OutputGroups` `OutputGroupDependencies` vardır. Visual Studio, proje çıkışlarının belirli listelerini almak için bu hedefleri çağırıyor. Örneğin hedef, `SatelliteDllsProjectOutputGroup` bir derlemenin oluşturacakları tüm uydu derlemelerinin listesini oluşturur. Bu çıkış grupları yayımlama, dağıtım ve projeden projeye başvurular gibi özellikler tarafından kullanılır. Bunları tanımlamadan projeler Visual Studio yüklensin ve Visual Studio ancak bazı özellikler düzgün çalışmayabilir.

## <a name="reference-resolution"></a>Başvuru çözümlemesi

 Başvuru çözümlemesi, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. Visual Studio, Özellikler penceresinde her başvuru için ayrıntılı özellikleri göstermek amacıyla başvuru çözümlemesi **tetiklemeli.** Aşağıdaki listede üç başvuru türü ve bunların nasıl çözümlenleri açıkmektedir.

- Derleme başvuruları:

   Proje sistemi, iyi bilinen adıyla bir hedef `ResolveAssemblyReferences` arar. Bu hedef, öğe türü adıyla öğeler `ReferencePath` üretmeli. Bu öğelerin her biri, başvuru yolunun tamamını içeren bir öğe belirtimi `Include` (bir öğenin özniteliğinin değeri) içerir. Öğeler, aşağıdaki yeni meta verilere ek olarak giriş öğelerinden geçirilen tüm meta verileri içerir:

  - `CopyLocal`, derlemenin çıkış klasörüne kopyalanmış olup olmadığını belirtir, true veya false olarak ayarlanır.

  - `OriginalItemSpec`, başvuru için özgün öğe belirtimlerini içerir.

  - `ResolvedFrom`, "{TargetFrameworkDirectory}" olarak ayarlanırsa, .NET Framework ayarlayın.

- COM başvuruları:

   Proje sistemi, iyi bilinen adıyla bir hedef `ResolveCOMReferences` arar. Bu hedef, öğe türü adıyla öğeler `ComReferenceWrappers` üretmeli. Bu öğelerin her biri, COM başvurusu için birlikte çalışma derlemesi yolunun tamamını içeren bir öğe belirtimlerine sahip olması gerekir. Öğelerde, derlemenin çıkış klasörüne kopyalanır mı, true mu yoksa false olarak ayar mı olacağını belirten, adına sahip yeni meta verilere ek olarak, giriş öğelerinden geçirilen tüm meta `CopyLocal` veriler bulunur.

- Yerel başvurular

   Proje sistemi, iyi bilinen adıyla bir hedef `ResolveNativeReferences` arar. Bu hedef, öğe türü adıyla öğeler `NativeReferenceFile` üretmeli. Öğeler, başvurunun özgün öğe belirtimlerini içeren adlı yeni bir meta veri parçasına ek olarak, giriş öğelerinden geçirilen tüm `OriginalItemSpec` meta verileri içerir.

## <a name="performance-shortcuts"></a>Performans kısayolları

 Hata ayıklamaya başlamak için Visual Studio IDE'yi kullanırsanız (F5 anahtarını seçerek veya menü çubuğunda Hata AyıklamaYı Başlat'ı seçerek) veya projenizi derlemek (derleme çözümü gibi), derleme işlemi performansı geliştirmek için hızlı bir güncelleştirme denetimi  >     >  kullanır. Özelleştirilmiş derlemelerin sırasıyla dosya oluşturması bazı durumlarda hızlı güncelleştirme denetimi değiştirilen dosyaları doğru şekilde tanımlamaz. Daha kapsamlı güncelleştirme denetimlerine ihtiyaç olan projeler, ortam değişkenlerini ayarerek hızlı denetimi devre dışı `DISABLEFASTUPTODATECHECK=1` bırakır. Alternatif olarak, projeler bunu projede veya projenin içeri aktaran bir dosyada MSBuild özelliği olarak ayarlayın.

 Visual Studio'daki normal derlemeler için hızlı güncelleştirme denetimi geçerli değildir ve proje, derlemeyi komut isteminde çağırıyor gibi derlemeyi yapacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapı Visual Studio genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [IDE'den derleme başlatma](../msbuild/starting-a-build-from-within-the-ide.md)
- [Dosyanın uzantılarını .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
- [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
