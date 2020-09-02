---
title: Visual Studio tümleştirmesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c90019aa24047524005ba70aa4f1aec75f89c71d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825418"
---
# <a name="visual-studio-integration-msbuild"></a>Visual Studio Tümleştirmesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Yönetilen projeleri yüklemek ve derlemek için Visual Studio ana bilgisayarları. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Projeden sorumlu olduğundan, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje farklı bir araç tarafından yazılmış ve özelleştirilmiş bir yapı işlemine sahip olsa bile, biçimdeki neredeyse tüm projeler ' de başarılı bir şekilde kullanılabilir.  
  
 Bu konuda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] yüklemek ve derlemek istediğiniz projeleri ve. targets dosyalarını özelleştirirken göz önünde bulundurmanız gereken belirli yönleri açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bunlar, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IntelliSense ve hata ayıklama gibi özelliklerin özel projeniz için çalışmasına emin olmanıza yardımcı olur.  
  
 C++ projeleri hakkında daha fazla bilgi için bkz. [proje dosyaları](/cpp/build/reference/project-files).  
  
## <a name="project-file-name-extensions"></a>Proje Dosya Adı Uzantıları  
 MSBuild.exe,. * proj düzeniyle eşleşen herhangi bir proje dosya adı uzantısını tanır. Ancak, projeyi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yükleyecek dile özgü proje sistemini belirleyen bu proje dosya adı uzantılarının yalnızca bir alt kümesini tanır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dilden bağımsız [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tabanlı bir proje sistemine sahip değildir.  
  
 Örneğin, [!INCLUDE[csprcs](../includes/csprcs-md.md)] Proje sistemi. csproj dosyalarını yükler, ancak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . xxproj dosyasını yükleyemez. Rastgele bir dildeki kaynak dosyaları için bir proje dosyası, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] ' de yüklenecek olan veya proje dosyaları ile aynı uzantıyı kullanmalıdır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="well-known-target-names"></a>İyi Bilinen Hedef Adları  
 İçindeki **Build** komutuna tıkladığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projede varsayılan hedef yürütülür. Genellikle, bu hedef de olarak adlandırılır `Build` . **Yeniden oluşturma** veya **Temizleme** komutunun seçilmesi, projede aynı ada sahip bir hedefi yürütmeye çalışır. **Yayımla** ' ya tıkladığınızda projede adlı bir hedef yürütülür `PublishOnly` .  
  
## <a name="configurations-and-platforms"></a>Yapılandırmalar ve Platformlar  
 Konfigürasyonlar, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bir özniteliği içeren bir öğede gruplanmış özelliklere göre projelerde temsil edilir `PropertyGroup` `Condition` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görüntülenecek proje yapılandırmalarının ve platformların bir listesini oluşturmak için bu koşullara bakar. Bu listeyi başarıyla ayıklamak için, koşulların aşağıdakine benzer bir biçimi olmalıdır:  
  
```  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]`PropertyGroup`Bu amaçla,,, `ItemGroup` `Import` özelliği ve öğe öğelerinin koşullarına bakar.  
  
## <a name="additional-build-actions"></a>Ek Yapı Eylemleri  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)][dosya özellikleri](https://msdn.microsoft.com/013c4aed-08d6-4dce-a124-ca807ca08959) penceresinin **Build Action** özelliği ile bir projedeki bir dosyanın öğe türü adını değiştirmenize izin verir. `Compile`, `EmbeddedResource` , `Content` ve `None` öğe türü adları her zaman bu menüde, projenizde zaten bulunan diğer öğe türü adlarıyla birlikte listelenir. Bu menüde her zaman özel öğe türü adlarının kullanılabilir olduğundan emin olmak için adları adlı bir öğe türüne ekleyebilirsiniz `AvailableItemName` . Örneğin, proje dosyanıza aşağıdakileri eklemek, `JScript` içeri aktarılan tüm projeler için özel türü bu menüye ekler:  
  
```  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
> Bazı öğe türü adları, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu açılan listede özel ancak listelenmez.  
  
## <a name="in-process-compilers"></a>İşlem İçi Derleyiciler  
 Mümkün olduğunda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] daha fazla performans için derleyicinin işlem içi sürümünü kullanmaya çalışır. (İçin geçerli değildir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .) Bunun düzgün çalışması için aşağıdaki koşulların karşılanması gerekir:  
  
- Projenin bir hedefinde, projeler için adlı bir görev olmalıdır `Vbc` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .  
  
- `UseHostCompilerIfAvailable`Görevin parametresi true olarak ayarlanmalıdır.  
  
## <a name="design-time-intellisense"></a>Tasarım Zamanı IntelliSense  
 Bir derleme bir çıkış derlemesi oluşturmadan önce ' de IntelliSense desteği almak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdaki koşulların karşılanması gerekir:  
  
- Adında bir hedef olması gerekir `Compile` .  
  
- `Compile`Hedefi veya bağımlılıklarından biri, proje için ya da gibi derleyici görevini çağırmalıdır `Csc` `Vbc` .  
  
- `Compile`Hedefi veya bağımlılıklarından biri, derleyicinin IntelliSense için gereken tüm parametreleri, özellikle de tüm başvuruları almasına neden olmalıdır.  
  
- "Işlem Içi derleyiciler" bölümünde listelenen koşullar sağlanmalıdır.  
  
## <a name="building-solutions"></a>Çözümler Oluşturma  
 İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , çözüm dosyası ve proje derleme sıralaması kendisi tarafından denetlenir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Komut satırında msbuild.exe bir çözüm oluştururken [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] çözüm dosyasını ayrıştırır ve proje yapılarını sıralar. Her iki durumda da, projeler bağımlılık sırasında tek tek oluşturulmuştur ve proje başvurularına proje başvurularına verilmez. Buna karşılık, tek tek projeler msbuild.exe ile oluşturulduğunda proje başvurularına proje başvurularına çapraz yapılır.  
  
 İçinde oluştururken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , özelliği `$(BuildingInsideVisualStudio)` olarak ayarlanır `true` . Bu, projede veya. targets dosyalarında, derleme 'in farklı davranmasına neden olacak şekilde kullanılabilir.  
  
## <a name="displaying-properties-and-items"></a>Özellikleri ve Öğeleri Görüntüleme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belirli özellik adlarını ve değerleri tanır. Örneğin, bir projedeki aşağıdaki özellik, **Windows uygulamasının** **Proje Tasarımcısı**'ndaki **uygulama türü** kutusunda görünmesine neden olur.  
  
```  
<OutputType>WinExe</OutputType>  
```  
  
 Özellik değeri **Proje tasarımcısında** düzenlenebilir ve proje dosyasına kaydedilebilir. Bu tür bir özelliğe el ile düzenleyerek geçersiz bir değer verilirse, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje yüklendiğinde bir uyarı gösterir ve geçersiz değeri varsayılan bir değerle değiştirir.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bazı özelliklerin varsayılan değerlerini anlamıştır. Bu özellikler, varsayılan olmayan değerlere sahip olmadıkları takdirde proje dosyasında kalıcı olmayacaktır.  
  
 Rastgele adlara sahip özellikler içinde görüntülenmez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . İçindeki rastgele özellikleri değiştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , proje dosyasını XML düzenleyicisinde açmanız ve bunları el ile düzenlemeniz gerekir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki [Visual Studio 'Da proje dosyalarını Düzenle](#BKMK_EditingProjects) bölümüne bakın.  
  
 Projesinde, rastgele öğe türü adlarıyla tanımlanmış öğeler, varsayılan olarak, Proje düğümleri altında Çözüm Gezgini görüntülenir. Bir öğeyi görüntüleme listesinden gizlemek için `Visible` meta verileri olarak ayarlayın `false` . Örneğin, aşağıdaki öğe derleme işlemine katılır, ancak Çözüm Gezgini gösterilmez.  
  
```  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Projeye içeri aktarılan dosyalarda belirtilen öğeler varsayılan olarak görüntülenmez. Yapı işlemi sırasında oluşturulan öğeler Çözüm Gezgini hiçbir şekilde gösterilmez.  
  
## <a name="conditions-on-items-and-properties"></a>Öğeler ve Özellikler İle İlgili Koşullar  
 Bir derleme sırasında tüm koşullar tam olarak işlenir.  
  
 Görüntülenecek özellik değerlerini belirlerken, yapılandırmaya bağımlı olan Özellikler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yapılandırmayı birbirinden bağımsız olarak kabul eden özelliklerden farklı şekilde değerlendirilir. Yapılandırmaya bağımlı olduğunu düşündüğü özellikler için, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] `Configuration` ve `Platform` özelliklerini uygun şekilde ayarlar ve [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projeyi yeniden değerlendirmesini söyler. Yapılandırmayı bağımsız olarak kabul eden özellikler için, koşulların nasıl değerlendirileceğini belirsiz hale gelir.  
  
 Öğelerin Çözüm Gezgini gösterilip gösterilmeyeceğine karar vermek amacıyla öğelerdeki Koşullu ifadeler her zaman göz ardı edilir.  
  
## <a name="debugging"></a>Hata Ayıklama  
 Çıkış derlemesini bulup başlatmak ve hata ayıklayıcıyı iliştirmek için, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] özelliklerine `OutputPath` `AssemblyName` ve `OutputType` doğru şekilde tanımlanmalıdır. Derleme işlemi derleyicinin bir. pdb dosyası oluşturmasına neden değilse, hata ayıklayıcısı iliştirilemiyor.  
  
## <a name="design-time-target-execution"></a>Tasarım Zamanı Hedef Yürütme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir projeyi yüklediğinde belirli adlarla hedefleri yürütmeye çalışır. Bu hedefler,,, `Compile` `ResolveAssemblyReferences` ve içerir `ResolveCOMReferences` `GetFrameworkPaths` `CopyRunEnvironmentFiles` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Derleyicinin IntelliSense sağlamak üzere başlatılabilmesi için bu hedefleri çalıştırır, hata ayıklayıcı başlatılabilir ve Çözüm Gezgini ' de görüntülenen başvuruların çözümlenebilmesini sağlayabilirsiniz. Bu hedefler yoksa, proje doğru şekilde yüklenir ve oluşturulur ancak içindeki tasarım zamanı deneyimi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tam olarak işlevsel olmayacaktır.  
  
## <a name="editing-project-files-in-visual-studio"></a><a name="BKMK_EditingProjects"></a> Visual Studio 'da proje dosyalarını Düzenle  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Projeyi doğrudan düzenlemek için, proje dosyasını Visual STUDIO XML düzenleyicisinde açabilirsiniz.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Visual Studio'da bir proje dosyasının yüklemesini kaldırmak ve düzenlemek için  
  
1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Projeyi Kaldır**' ı seçin.  
  
     Proje işaretlendi **(kullanılamıyor)**.  
  
2. **Çözüm Gezgini**' de, kullanılamayan proje için kısayol menüsünü açın ve ardından **Düzenle \<Project File> **' yi seçin.  
  
     Proje dosyası Visual Studio XML düzenleyicisinde açılır.  
  
3. Proje dosyasını düzenleyin, kaydedin ve ardından kapatın.  
  
4. **Çözüm Gezgini**' de, kullanılamayan proje için kısayol menüsünü açın ve ardından **projeyi yeniden yükle**' yi seçin.  
  
## <a name="intellisense-and-validation"></a>IntelliSense ve Doğrulama  
 Proje dosyalarını düzenlemek için XML düzenleyicisini kullanırken, IntelliSense ve doğrulama, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] şema dosyaları tarafından çalıştırılır. Bunlar, *\<Visual Studio installation directory>* \Xml\schemas\1010\msbuilddizininde bulunan şema önbelleğine yüklenir.  
  
 Temel türler Microsoft. Build. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Core. xsd ve tarafından kullanılan ortak türlerde tanımlanmıştır, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Microsoft. Build. CommonTypes. xsd dosyasında tanımlanmıştır. Şemaları, özel öğe türü adları, özellikleri ve görevleri için IntelliSense ve doğrulamaya sahip olacak şekilde özelleştirmek için Microsoft. Build. xsd ' yi düzenleyebilir ya da CommonTypes veya Core şemalarını içeren kendi şemanızı oluşturabilirsiniz. Kendi şemanızı oluşturursanız, **Özellikler** penceresini kullanarak bulmak için XML düzenleyicisini yönlendirirsiniz.  
  
## <a name="editing-loaded-project-files"></a>Yüklenmiş Proje Dosyalarını Düzenleme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje dosyaları ve proje dosyaları tarafından içeri aktarılan dosyaların içeriğini önbelleğe alır. Yüklenen bir proje dosyasını düzenlerseniz, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] değişikliklerin etkili olması için otomatik olarak projeyi yeniden yüklemenizi ister. Ancak, yüklenen bir proje tarafından içeri aktarılan bir dosyayı düzenlerseniz, yeniden yükleme istemi olmaz ve değişikliklerin etkili olması için projeyi el ile kaldırıp yeniden yüklemeniz gerekir.  
  
## <a name="output-groups"></a>Çıkış Grupları  
 Microsoft. Common. targets içinde tanımlanan birçok hedef, veya ile biten adlara sahiptir `OutputGroups` `OutputGroupDependencies` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje çıkışları için belirli listeleri almak üzere bu hedefleri çağırır. Örneğin, hedef, `SatelliteDllsProjectOutputGroup` derleme oluşturulacak tüm uydu derlemelerinin listesini oluşturur. Bu çıktı grupları, proje başvurularına yayımlama, dağıtım ve proje gibi özellikler tarafından kullanılır. Onları tanımlamayan projeler içinde yüklenir ve oluşturulur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ancak bazı özellikler düzgün çalışmayabilir.  
  
## <a name="reference-resolution"></a>Başvuru Çözümleme  
 Başvuru çözümleme, gerçek derlemeleri bulmak için bir proje dosyasında depolanan başvuru öğelerini kullanma işlemidir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , **Özellikler** penceresindeki her bir başvurunun ayrıntılı özelliklerini göstermek için başvuru çözümlemesi tetiklemelidir. Aşağıdaki listede, üç tür başvuru ve nasıl çözümlendikleri açıklanmaktadır.  
  
- Bütünleştirilmiş kod başvuruları:  
  
  Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveAssemblyReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `ReferencePath` . Bu öğelerin her biri, `Include` başvurunun tam yolunu içeren bir öğe belirtimine (bir öğenin özniteliğinin değeri) sahip olmalıdır. Öğelerin, aşağıdaki yeni meta verilere ek olarak, geçirilen giriş öğelerinden tüm meta verilere sahip olması gerekir:  

  - `CopyLocal`, derlemenin çıkış klasörüne kopyalanıp kopyalanmayacağını belirtir, true veya false olarak ayarlayın.  

  - `OriginalItemSpec`, başvurunun orijinal öğe belirtimini içeren.  

  - `ResolvedFrom`, dizinden çözümlenmişse "{TargetFrameworkDirectory}" olarak ayarlanır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
- COM başvuruları:  
  
     Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveCOMReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `ComReferenceWrappers` . Bu öğelerin her biri, COM başvurusunun birlikte çalışma derlemesine tam yolu içeren bir öğe belirtimine sahip olmalıdır. Öğelerin, bir ada sahip yeni meta verilere ek olarak,, `CopyLocal` derlemenin çıkış klasörüne kopyalanıp kopyalanmayacağını belirten, true veya false olarak ayarlandığından  
  
- Yerel başvurular  
  
     Proje sistemi, iyi bilinen ada sahip bir hedef çağırır `ResolveNativeReferences` . Bu hedef öğe türü adına sahip öğeler üretmelidir `NativeReferenceFile` . Öğelerin, `OriginalItemSpec` başvurunun orijinal öğe belirtimini içeren, adlı yeni bir meta veri parçasına ek olarak, geçirilen giriş öğelerinden tüm meta verilere sahip olması gerekir.  
  
## <a name="performance-shortcuts"></a>Performans Kısayolları  
 Visual Studio Kullanıcı arabiriminde hata ayıklamayı başlatırsanız (F5 tuşunu seçerek veya **Hata Ayıkla**, menü çubuğunda **hata ayıklamayı Başlat** ' ı seçerek), yapı işlemi performansı artırmak için hızlı bir güncelleştirme denetimi kullanır. Özelleştirilmiş yapıların, yerleşik olarak oluşturulan dosyalar oluşturmasındaki bazı durumlarda, hızlı güncelleştirme denetimi değiştirilen dosyaları doğru şekilde tanımlamaz. Daha kapsamlı güncelleştirme denetimleri gerektiren projeler, ortam değişkenini ayarlayarak hızlı denetlemeyi kapatabilir `DISABLEFASTUPTODATECHECK=1` . Alternatif olarak, projeler bunu projede veya projenin içeri aktardığı bir dosyada MSBuild özelliği olarak ayarlayabilir.  
  
 Visual Studio 'daki normal derlemeler için hızlı güncelleştirme denetimi uygulanmaz ve proje, derlemeyi bir komut isteminde çağırırı olarak derler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Visual Studio derleme Işlemini genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [IDE içinden derleme başlatma](../msbuild/starting-a-build-from-within-the-ide.md)   
 [.NET Framework uzantıları kaydediliyor](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [Item öğesi (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Property öğesi (MSBuild)](../msbuild/property-element-msbuild.md)   
 [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Csc görevi](../msbuild/csc-task.md)   
 [Vbc görevi](../msbuild/vbc-task.md)
