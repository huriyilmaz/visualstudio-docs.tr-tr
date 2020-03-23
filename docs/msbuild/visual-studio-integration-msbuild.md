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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631204"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio entegrasyonu (MSBuild)

Visual Studio, yönetilen projeleri yüklemek ve oluşturmak için MSBuild'e ev sahipliği yapmaktadır. MSBuild projeden sorumlu olduğundan, MSBuild formatındaki hemen hemen her proje Visual Studio'da başarıyla kullanılabilir, proje farklı bir araç tarafından yazılmış ve özelleştirilmiş bir yapı sürecine sahip olsa bile.

 Bu makalede, Visual Studio'nun MSBuild barındırma sının, Visual Studio'da yüklemek ve oluşturmak istediğiniz projeleri ve *.hedefleri* özelleştirirken göz önünde bulundurulması gereken belirli yönleri açıklanmaktadır. Bunlar, IntelliSense ve hata ayıklama gibi Visual Studio özelliklerinin özel projeniz için çalışmasını sağlamanıza yardımcı olur.

 C++ projeleri hakkında bilgi için [Project dosyalarına](/cpp/build/reference/project-files)bakın.

## <a name="project-file-name-extensions"></a>Proje dosya adı uzantıları

 *MSBuild.exe* desen eşleşen herhangi bir proje dosya adı uzantısı *tanır.\* proj*. Ancak Visual Studio, projeyi yükleyecek dile özgü proje sistemini belirleyen bu proje dosya adı uzantılarının bir alt kümesini tanır. Visual Studio'da dilden bağımsız MSBuild tabanlı proje sistemi yoktur.

 Örneğin, C# proje sistemi *.csproj* dosyalarını yükler, ancak Visual Studio *bir .xxproj* dosyasını yükleyemez. Rasgele bir dilde kaynak dosyaları için bir proje dosyası Visual Studio yüklenecek Visual Basic veya C# proje dosyaları ile aynı uzantı yı kullanmalıdır.

## <a name="well-known-target-names"></a>Tanınmış hedef adları

 Visual Studio'da **Yapı** komutunu tıklattığınızda projedeki varsayılan hedef yürütülür. Genellikle, bu hedef `Build`de adlandırılır. **Yeniden Oluştur** veya **Temizle** komutunu seçmek, projede aynı adı taşıyan bir hedefi yürütmeye çalışır. **Yayımla'yı** tıklatarak `PublishOnly` projede adı geçen bir hedef yürütülür.

## <a name="configurations-and-platforms"></a>Yapılandırmalar ve platformlar

 Yapılandırmalar MSBuild projelerinde bir `PropertyGroup` `Condition` öznitelik içeren bir öğe yle gruplanmış özelliklerle temsil edilir. Visual Studio, görüntülenecek proje yapılandırmaları ve platformların bir listesini oluşturmak için bu koşullara bakar. Bu listeyi başarıyla ayıklamak için koşulların aşağıdakilere benzer bir biçime sahip olması gerekir:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio bu amaç `PropertyGroup` `ItemGroup`için `Import`, , , özellik ve öğe öğeleri üzerinde koşullara bakar.

## <a name="additional-build-actions"></a>Ek yapı eylemleri

 Visual Studio, **Dosya özellikleri** penceresinin **Eylem Oluştur** özelliğiyle projedeki bir dosyanın öğe türü adını değiştirmenize olanak tanır. **Derleme**, **EmbeddedResource**, **İçerik**ve **Hiçbiri** öğe türü adları her zaman bu menüde, projenizde bulunan diğer öğe türü adlarıyla birlikte listelenir. Bu menüde özel madde türü adlarının her zaman kullanılabilir olduğundan emin `AvailableItemName`olmak için, adları bir öğe türüne ekleyebilirsiniz. Örneğin, proje dosyanıza aşağıdakileri eklemek, bu menüye özel **JScript** türünü içe aktaran tüm projeler için ekler:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Bazı öğe türü adları Visual Studio için özeldir, ancak bu açılır listede yer almamaktadır.

## <a name="in-process-compilers"></a>Süreç içi derleyiciler

 Mümkün olduğunda, Visual Studio artan performans için Visual Basic derleyicisinin işlem içi sürümünü kullanmaya çalışır. (C#için geçerli değildir.) Bunun doğru çalışması için aşağıdaki koşulların yerine getirilmesi gerekir:

- Projenin bir hedefinde, Visual Basic projeleri `Vbc` için bir görev olmalıdır.

- Görevin `UseHostCompilerIfAvailable` parametresi doğru olarak ayarlanmalıdır.

## <a name="design-time-intellisense"></a>Tasarım zamanı IntelliSense

 Bir yapı bir çıktı derlemesi oluşturmadan önce Visual Studio'da IntelliSense desteği almak için aşağıdaki koşulların karşılanması gerekir:

- Adında `Compile`bir hedef olmalı.

- Hedef `Compile` veya bağımlılıklarından biri, proje için derleyici görevini çağırmalıdır, `Vbc`örneğin. `Csc`

- `Compile` Hedef veya bağımlılıklarından biri derleyicinin IntelliSense için gerekli tüm parametreleri, özellikle de tüm başvuruları almasına neden olmalıdır.

- [Süreç içi derleyiciler](#in-process-compilers) bölümünde listelenen koşullar karşılanmalıdır.

## <a name="build-solutions"></a>Çözüm oluşturma

 Visual Studio içinde, çözüm dosyası ve proje oluşturma siparişi Visual Studio'nun kendisi tarafından denetlenir. Komut satırında *msbuild.exe* ile bir çözüm oluştururken, MSBuild çözüm dosyasını ayrıştırır ve projenin oluşturmasını emreder. Her iki durumda da projeler bağımlılık sırasına göre ayrı ayrı oluşturulur ve proje dentekiler için proje başvuruları geçilemez. Buna karşılık, tek tek projeler *msbuild.exe*ile inşa edildiğinde, proje den proje referansları geçilir.

 Visual Studio içinde inşa `$(BuildingInsideVisualStudio)` ederken, `true`özellik ayarlanır . Bu, yapının farklı davranmasına neden olmak için projenizde veya *.hedefler* dosyalarınızda kullanılabilir.

## <a name="display-properties-and-items"></a>Özellikleri ve öğeleri görüntüleme

 Visual Studio belirli özellik adlarını ve değerlerini tanır. Örneğin, projedeki aşağıdaki **özellik, Windows Uygulamasının** **Proje Tasarımcısı'ndaki** **Uygulama Türü** kutusunda görünmesine neden olur.

```xml
<OutputType>WinExe</OutputType>
```

 Özellik değeri **Proje Tasarımcısı'nda** düzenlenebilir ve proje dosyasına kaydedilebilir. Böyle bir özellik el düzenleme tarafından geçersiz bir değer verilirse, Visual Studio proje yüklendiğinde bir uyarı gösterir ve geçersiz değeri varsayılan bir değerle değiştirir.

 Visual Studio, bazı özellikler için varsayılanları anlar. Bu özellikler, varsayılan olmayan değerlere sahip olmadıkları sürece proje dosyasında kalıcı olmayacaktır.

 Rasgele adlar içeren özellikler Visual Studio'da görüntülenmez. Visual Studio'daki rasgele özellikleri değiştirmek için XML düzenleyicisinde proje dosyasını açmanız ve bunları elle düzenlemeniz gerekir. Daha fazla bilgi için, bu konunun ilerleyen bölümlerinde Visual Studio bölümündeki [proje dosyalarını edit](#edit-project-files-in-visual-studio) bölümüne bakın.

 Projede rasgele madde türü adlarıyla tanımlanan öğeler varsayılan olarak **Çözüm Gezgini'nde** proje düğümleri altında görüntülenir. Bir öğeyi ekrandan gizlemek `Visible` için `false`meta verileri ' ye ayarlayın. Örneğin, aşağıdaki öğe yapı işlemine katılır, ancak **Çözüm Gezgini'nde**görüntülenmez.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Meta `Visible` veriler C++ projeleri için **Solution Explorer** tarafından yoksayılır. Öğeler her zaman yanlış `Visible` olarak ayarlanmış olsa bile gösterilir.

 Projeye alınan dosyalarda bildirilen öğeler varsayılan olarak görüntülenmez. Yapı işlemi sırasında oluşturulan öğeler **Çözüm Gezgini'nde**asla görüntülenmez.

## <a name="conditions-on-items-and-properties"></a>Maddeler ve özelliklerle ilgili koşullar

 Bir yapı sırasında, tüm koşullar adedine tam olarak uyulmaktadır.

 Görüntülenecek özellik değerleri belirlenirken, Visual Studio'nun yapılandırmaya bağımlı olarak gördüğü özellikler, yapılandırmayı bağımsız olarak gördüğü özelliklerden farklı şekilde değerlendirilir. Yapılandırmaya bağımlı olduğunu düşündüğü özellikler için `Configuration` `Platform` Visual Studio, özellikleri ve özellikleri uygun şekilde ayarlar ve MSBuild'e projeyi yeniden değerlendirmesini bildirir. Yapılandırmayı bağımsız olarak gördüğü özellikler için, koşulların nasıl değerlendirileceği belirsizdir.

 Öğelerdeki koşullu ifadeler, öğenin **Çözüm Gezgini'nde**görüntülenip görüntülenmeyacağına karar vermek amacıyla her zaman yoksayılır.

## <a name="debugging"></a>Hata ayıklama

 Çıktı montajını bulmak ve başlatmak ve hata ayıklamayı takmak `OutputPath` `AssemblyName`için `OutputType` Visual Studio'nun , ve doğru tanımlanmış özelliklere ihtiyacı vardır. Derleme işlemi derleyicinin *.pdb* dosyası oluşturmasına neden olmadıysa hata ayıklayıcı eklenmez.

## <a name="design-time-target-execution"></a>Tasarım zamanı hedef yürütme

 Visual Studio, bir proje yüklerken belirli adlarla hedefleri yürütmeye çalışır. Bu hedefler `Compile` `ResolveAssemblyReferences`arasında `ResolveCOMReferences` `GetFrameworkPaths`, `CopyRunEnvironmentFiles`, , , ve . Visual Studio bu hedefleri, derleyicinin IntelliSense'i sağlamak için başlatılmasını, hata ayıklayıcının başlatılmasını ve Solution Explorer'da görüntülenen başvuruların çözümlenebilmesi için çalıştırılır. Bu hedefler mevcut değilse, proje yüklenir ve doğru bir şekilde inşa edilir, ancak Visual Studio'daki tasarım zamanı deneyimi tam olarak işlevsel olmayacaktır.

## <a name="edit-project-files-in-visual-studio"></a>Visual Studio'da proje dosyalarını düzenlemesi

 Bir MSBuild projesini doğrudan yeniden oluşturmak için Visual Studio XML düzenleyicisinde proje dosyasını açabilirsiniz.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için

1. **Çözüm Gezgini'nde,** proje için kısayol menüsünü açın ve ardından **Project'i Boşalt'ı**seçin.

     Proje işaretlenir **(kullanılamaz)**.

2. **Çözüm Gezgini'nde,** kullanılamayan proje için kısayol menüsünü açın ve ardından Project **File>'yı \<edit'i **seçin.

     Proje dosyası Visual Studio XML Düzenleyicisi'nde açılır.

3. Proje dosyasını edin, kaydedin ve kapatın.

4. **Çözüm Gezgini'nde,** kullanılamayan proje için kısayol menüsünü açın ve ardından **Project'i Yeniden Yükle'yi**seçin.

## <a name="intellisense-and-validation"></a>IntelliSense ve doğrulama

 Proje dosyalarını düzenlemek için XML düzenleyicisini kullanırken, IntelliSense ve doğrulama MSBuild şema dosyaları tarafından yönlendirilir. Bunlar Visual Studio yükleme dizininde bulunan şema önbelleğine yüklenir * \<>\Xml\Schemas\1033\MSBuild*.

 Çekirdek MSBuild türleri *Microsoft.Build.Core.xsd* ve Visual Studio tarafından kullanılan yaygın türleri *Microsoft.Build.CommonTypes.xsd*tanımlanır tanımlanır. Özel madde türü adları, özellikleri ve görevler için IntelliSense ve doğrulama olacak şekilde şemaları özelleştirmek için *Microsoft.Build.xsd'yi*veya CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Kendi şemanızı oluşturursanız, **Özellikler** penceresini kullanarak bulmak için XML düzenleyicisini yönlendirmeniz gerekir.

## <a name="edit-loaded-project-files"></a>Yüklenen proje dosyalarını düzenlemesi

 Visual Studio, proje dosyaları tarafından içe aktarılan proje dosyalarının ve dosyaların içeriğini önbelleğe alıntır. Yüklü bir proje dosyasını yeniden doldurursanız, Visual Studio değişikliklerin etkili olması için projeyi otomatik olarak yeniden yüklemenizi ister. Ancak, yüklenen bir proje tarafından içe aktarılan bir dosyayı düzenlemeniz, yeniden yükleme istemi olmaz ve değişikliklerin etkin hale gelabilmesi için projeyi el ile kaldırmanız ve yeniden yüklemeniz gerekir.

## <a name="output-groups"></a>Çıktı grupları

 *Microsoft.Common.targets'da* tanımlanan birkaç hedefin adları bitiş `OutputGroups` veya `OutputGroupDependencies`. Visual Studio, proje çıktılarının belirli listelerini almak için bu hedefleri çağırır. Örneğin, `SatelliteDllsProjectOutputGroup` hedef, bir yapının oluşturacağı tüm uydu derlemelerinin bir listesini oluşturur. Bu çıktı grupları, proje başvuruları için yayımlama, dağıtım ve proje gibi özellikler tarafından kullanılır. Bunları tanımlamayan projeler Visual Studio'da yüklenir ve inşa edecektir, ancak bazı özellikler doğru çalışmayabilir.

## <a name="reference-resolution"></a>Referans çözünürlüğü

 Başvuru çözümü, gerçek derlemeleri bulmak için proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. Visual Studio, **Özellikler** penceresindeki her başvuru için ayrıntılı özellikleri göstermek için başvuru çözümünü tetiklemelidir. Aşağıdaki listede üç başvuru türü ve bunların nasıl çözüldüğü açıklanmaktadır.

- Montaj başvuruları:

   Proje sistemi tanınmış adı `ResolveAssemblyReferences`olan bir hedef çağırır. Bu hedef, madde türü adı `ReferencePath`olan maddeler üretmelidir. Bu öğelerin her biri, başvuruya giden `Include` tam yolu içeren bir madde belirtimine (maddenin özniteliğinin değeri) sahip olmalıdır. Öğeler, aşağıdaki yeni meta verilere ek olarak giriş öğelerinden tüm meta verilere sahip olmalıdır:

  - `CopyLocal`, derlemenin çıktı klasörüne kopyalanıp doğru veya yanlış olarak ayarlanması gerektiğini gösterir.

  - `OriginalItemSpec`, başvurunun özgün madde belirtimini içeren.

  - `ResolvedFrom`,.NET Framework dizininden çözülmüşse "{TargetFrameworkDirectory}" olarak ayarlayın.

- COM referansları:

   Proje sistemi tanınmış adı `ResolveCOMReferences`olan bir hedef çağırır. Bu hedef, madde türü adı `ComReferenceWrappers`olan maddeler üretmelidir. Bu öğelerin her biri COM başvurusu için interop derlemesine tam yolu içeren bir madde belirtimi olmalıdır. Öğeler, derlemenin doğru veya yanlış olarak ayarlanmış çıktı klasörüne kopyalanması gerekip gerekmediğini belirten, adındaki `CopyLocal`yeni meta verilere ek olarak, giriş öğelerinden tüm meta verilere sahip olmalıdır.

- Yerel referanslar

   Proje sistemi tanınmış adı `ResolveNativeReferences`olan bir hedef çağırır. Bu hedef, madde türü adı `NativeReferenceFile`olan maddeler üretmelidir. Öğeler, başvurunun özgün madde belirtimini içeren yeni bir meta veri `OriginalItemSpec`parçasına ek olarak, giriş öğelerinden tüm meta verilere sahip olmalıdır.

## <a name="performance-shortcuts"></a>Performans kısayolları

 Görsel Studio IDE'yi hata ayıklamaya başlamak için (F5 tuşunu seçerek veya menü çubuğunda **Hata Ayıklama** > **Başlatma'yı** seçerek) veya projenizi oluşturmak için (örneğin, **Build** > **Solution)** oluşturursanız, yapı işlemi performansı artırmak için hızlı güncelleştirme denetimi kullanır. Özelleştirilmiş yapılar sırayla oluşturulan dosyaları oluşturmak bazı durumlarda, hızlı güncelleştirme denetimi değiştirilen dosyaları doğru tanımlamaz. Daha kapsamlı güncelleştirme denetimleri gerektiren projeler, ortam değişkenini `DISABLEFASTUPTODATECHECK=1`ayarlayarak hızlı denetimi kapatabilir. Alternatif olarak, projeler bunu projede veya proje içe aktaran bir dosyada MSBuild özelliği olarak ayarlayabilir.

 Visual Studio'daki düzenli yapılar için hızlı güncelleştirme denetimi geçerli değildir ve proje, yapıyı komut isteminde çağırılmış gibi oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl?](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [IDE içinden bir yapı başlatın](../msbuild/starting-a-build-from-within-the-ide.md)
- [.NET Çerçevesi'nin uzantılarını kaydedin](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
- [Hedef eleman (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Vbc görevi](../msbuild/vbc-task.md)
