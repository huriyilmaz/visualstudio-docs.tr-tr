---
title: ÇözümmontajReferans Görevi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveAssemblyReference
- MSBuild.ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects
- MSBuild.ResolveAssemblyReference.FoundConflict
- MSBuild.ResolveAssemblyRedirects.SuggestedRedirects
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveAssemblyReference task [MSBuild]
- MSBuild, ResolveAssemblyReference task
ms.assetid: 4d56d848-b29b-4dff-86a2-0a96c9e4a170
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b79bd8eb3f7d813e3acd091ce5f2ffbc7b3eeb49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632764"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference görevi

İkinci ve `n`ikinci sıra bağımlılıkları da dahil olmak üzere belirtilen derlemelere bağlı tüm derlemeleri belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `ResolveAssemblyReference` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|İsteğe bağlı `String[]` parametre.<br /><br /> Başvuruları çözerken kullanılacak derleme dosyası adı uzantıları. Varsayılan dosya adı uzantıları *.exe* ve *.dll'dir.*|
|`AllowedRelatedFileExtensions`|İsteğe bağlı `String[]` parametre.<br /><br /> Birbiriyle ilişkili dosyaları aramak için kullanılacak dosya adı uzantıları. Varsayılan uzantılar *.pdb* ve *.xml'dir.*|
|`AppConfigFile`|İsteğe bağlı `String` parametre.<br /><br /> Ayırma ve ayıklamak için bağlayıcıRedirect eşlemeleri için bir *app.config* dosyası belirtir. Bu parametre belirtilirse, `AutoUnify` parametre `false`.|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Tam yolların ve bağımlılıkların tanımlanması gereken öğeleri belirtir. Bu öğeler "Sistem" gibi basit adlara veya "System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" gibi güçlü adlara sahip olabilir.<br /><br /> Bu parametreye geçirilen öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerine sahip olabilir:<br /><br /> -   `Private`: `Boolean` değer. , `true`öğe yerel olarak kopyalanırsa. Varsayılan değer: `true`.<br />-   `HintPath`: `String` değer. Başvuru olarak kullanılacak yol ve dosya adını belirtir. Bu meta veriler `SearchPaths` parametrede {HintPathFromItem} belirtildiğinde kullanılır. Varsayılan değer boş bir dizedir.<br />-   `SpecificVersion`: `Boolean` değer. Eğer, `true`daha sonra öznitelik `Include` belirtilen tam adı eşleşmelidir. Eğer `false`, sonra aynı basit ada sahip herhangi bir derleme çalışacaktır. `SpecificVersion` Belirtilmemişse, görev maddenin özniteliğindeki `Include` değeri inceler. Öznitelik basit bir adsa, öyle gibi `SpecificVersion` `false`olur. Öznitelik güçlü bir ad ise, `SpecificVersion` sanki . `true`<br />     Bir Başvuru öğesi türüyle `Include` kullanıldığında, özniteliğin çözülmesi için derlemenin tam birleştirme adı olması gerekir. Derleme yalnızca birleştirme özniteliğe tam `Include` olarak uyuyorsa çözülür.<br />     Bir proje bir .NET Framework sürümünü hedeflediğinde ve daha yüksek bir .NET Framework sürümü `SpecificVersion` için `true`derlenmiş bir derlemeye başvuruyorsa, başvuru yalnızca .<br />     Bir proje bir profili hedeflediğinde ve profilde olmayan bir derlemeye başvuruyorsa, başvuru yalnızca `SpecificVersion` `true`' olarak ayarlanmışsa çözülür.<br />-   `ExecutableExtension`: `String` değer. Varsa, çözümlenmiş derleme bu uzantıya sahip olmalıdır. Yokken, *.dll* önce kabul edilir, ardından incelenen her dizin için *.exe.*<br />-   `SubType`: `String` değer. Yalnızca boş Alt Yazı meta verileri olan öğeler tam derleme yollarına çözülür. Boş olmayan Alt Yazı meta verileri olan öğeler yoksayılır.<br />-   `AssemblyFolderKey`: `String` değer. Bu meta veriler eski amaçlar için desteklenir. Bu **hklm\\\<VendorFolder>** gibi kullanıcı tanımlı bir kayıt `Assemblies` defteri anahtarı, derleme başvuruları çözmek için kullanmanız gereken belirtir.|
|`AssemblyFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bağımlılıkları bulmak için tam nitelikli derlemelerin listesini belirtir.<br /><br /> Bu parametreye geçirilen öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerine sahip olabilir:<br /><br /> -   `Private`: isteğe bağlı `Boolean` bir değer. Doğruysa, öğe yerel olarak kopyalanır.<br />-   `FusionName`: `String` isteğe bağlı meta veriler. Bu öğe için basit veya güçlü adı belirtir. Bu öznitelik varsa, derleme dosyası nın adı almak için açılması gerekmedığından zaman kazandırabilir.|
|`AutoUnify`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre, normal bir *App.Config* dosyasına sahip olmayan DL'ler gibi derlemeler oluşturmak için kullanılır.<br /><br /> AppConfigFile parametresine geçirilen bir `true` *App.Config* dosyası varmış gibi otomatik olarak ele alınınca. Bu sanal *App.Config* dosyası, en yüksek sürüm derlemesinin seçileceği her çakışan derleme ler kümesi için bir bağlayıcıRedirect girişine sahiptir. Bunun bir sonucu da, her çatışma çözülmüş olacağı için, çakışan meclisler hakkında hiçbir zaman bir uyarı nın olmamasıdır.<br /><br /> Ne `true`zaman , her farklı remapping eski ve yeni sürümleri `AutoUnify` gösteren `true`yüksek öncelikli bir yorum neden olacak ve bu oldu .<br /><br /> AppConfigFile `true`parametresi boş olduğunda.<br /><br /> Ne `false`zaman , hiçbir derleme sürümü yeniden eşleme otomatik olarak oluşur. Bir derlemenin iki sürümü olduğunda, bir uyarı verilir.<br /><br /> Ne `false`zaman, aynı derleme farklı sürümleri arasında her ayrı çakışma yüksek öncelikli bir açıklama sonuçlanır. Bu yorumları tek bir uyarı takip edilir. Uyarının benzersiz bir hata kodu vardır ve "Başvurunun farklı sürümleri ile bağımlı derlemeler arasındaki çakışmaları buldu" yazan bir metin içerir.<br /><br /> Varsayılan değer: `false`.|
|`CandidateAssemblyFiles`|İsteğe bağlı `String[]` parametre.<br /><br /> Arama ve çözümleme işlemi için kullanılacak derlemelerin listesini belirtir. Bu parametreye geçirilen değerler mutlak dosya adları veya proje yle ilgili dosya adları olmalıdır.<br /><br /> Bu listedeki derlemeler, `SearchPaths` parametrede {CandidateAssemblyFiles} varsa göz önünde bulundurulması gereken yollardan biri olarak dikkate alınır.|
|`CopyLocalDependenciesWhenParentReferenceInGac`|İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> Doğruysa, bir bağımlılığın yerel olarak kopyalanması gerekip gerekip gerekmediğini belirlemek için yapılan denetimlerden biri, proje dosyasındaki ana başvurunun Özel meta veri kümesine sahip olup olmadığını görmektir. Ayarlanırsa, Özel değer bağımlılık olarak kullanılır.<br /><br /> Meta veriler ayarlanmazsa, bağımlılık üst başvuruyla aynı denetimlerden geçer. Bu denetimlerden biri, başvurunun GAC'de olup olmadığını görmektir. Bir başvuru GAC'deyse, hedef makinede GAC'de olduğu varsayıldığı için yerel olarak kopyalanmaz. Bu yalnızca belirli bir başvuru için geçerlidir, bağımlılıkları için değil.<br /><br /> Örneğin, PROJE dosyasındaki GAC'de bulunan bir başvuru yerel olarak kopyalanmaz, ancak GAC'de olmadıkları için bağımlılıkları yerel olarak kopyalanır.<br /><br /> Yanlışsa, proje dosyası başvuruları GAC'de olup olmadıklarını görmek için denetlenir ve uygun şekilde yerel olarak kopyalanır.<br /><br /> Bağımlılıklar GAC'de olup olmadıklarını görmek için denetlenir ve proje dosyasındaki üst başvurunun GAC'de olup olmadığını görmek için de denetlenir.<br /><br /> Proje dosyasındaki üst başvuru GAC'deyse, bağımlılık yerel olarak kopyalanmaz.<br /><br /> Bu parametre doğru veya yanlış olup olmadığını, birden çok üst başvuru varsa ve bunlardan herhangi biri GAC'de değilse, bunların tümü yerel olarak kopyalanır.|
|`CopyLocalFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> `ResolvedFiles` `ResolvedDependencyFiles` `RelatedFiles` `SatelliteFiles` `ScatterFiles` `true`Madde meta verileri olan ve değeri olan her dosyayı , , , ve parametreleri döndürür. `CopyLocal`|
|`FilesWritten`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Diske yazılan öğeleri içerir.|
|`FindDependencies`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`bağımlılıklar bulunur. Aksi takdirde, yalnızca birincil başvurular bulunur. Varsayılan değer: `true`.|
|`FindRelatedFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> If `true`, *.pdb* dosyaları ve *xml* dosyaları gibi ilgili dosyalar bulunur. Varsayılan değer: `true`.|
|`FindSatellites`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, uydu meclisleri bulunacaktır. Varsayılan değer: `true.`|
|`FindSerializationAssemblies`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, sonra görev serileştirme derlemeleri arar. Varsayılan değer: `true`.|
|`FullFrameworkAssemblyTables`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Redist listesini belirli bir çerçeve diziniyle ilişkilendirmek için "FrameworkDirectory" meta verilerine sahip öğeleri belirtir. İlişkilendirme yapılmazsa, bir hata günlüğe kaydedilir. Çözüm derlemesi başvurusu (RAR) mantığı, FrameworkDirectory ayarlanmazsa hedef çerçeve dizinini kullanır.|
|`FullFrameworkFolders`|İsteğe bağlı <xref:System.String?displayProperty=fullName> `[]` parametre.<br /><br /> RedistList dizinini içeren klasörleri belirtir. Bu dizin, belirli bir istemci profili için tam çerçeveyi temsil eder, örneğin, *%programdosyaları%\reference derlemeleri\microsoft\framework\v4.0*.|
|`FullTargetFrameworkSubsetNames`|İsteğe bağlı `String[]` parametre.<br /><br /> Hedef çerçeve alt kümesi adlarının listesini içerir. Listedeki bir alt küme adı `TargetFrameworkSubset` ad özelliğindekiyle eşleşirse, sistem oluşturma zamanında belirli hedef çerçeve alt kümesini hariç tutar.|
|`IgnoreDefaultInstalledAssemblyTables`|İsteğe bağlı `Boolean` parametre.<br /><br /> ', `true`görev , *\RedistList* dizininde bulunan ek yüklü montaj tablolarını (veya "Redist Listeleri") `TargetFrameworkDirectories`arar ve kullanırsa. Varsayılan değer: `false.`|
|`IgnoreDefaultInstalledAssemblySubsetTables`|İsteğe bağlı `Boolean` parametre.<br /><br /> ', `true`görev , *\SubsetList* dizininde bulunan ek yüklü montaj alt kümesi tablolarını (veya "Alt Küme `TargetFrameworkDirectories`Listeleri") arar ve kullanırsa. Varsayılan değer: `false.`|
|`InstalledAssemblySubsetTables`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Hedef alt kümede olması beklenen derlemeleri belirten XML dosyalarının listesini içerir.<br /><br /> Bir seçenek olarak, bu listedeki öğeler bir ilişkilendirmek için "FrameworkDirectory" meta verilerini belirtebilir`InstalledAssemblySubsetTable`<br /><br /> belirli bir çerçeve dizini ile.<br /><br /> Yalnızca bir `TargetFrameworkDirectories` öğe varsa, bu listede "FrameworkDirectory" meta verilerinden yoksun olan öğeler, geçirilen benzersiz değere `TargetFrameworkDirectories`ayarlanmış gibi değerlendirilir.|
|`InstalledAssemblyTables`|İsteğe bağlı `String` parametre.<br /><br /> Hedef bilgisayara yüklenmesi beklenen derlemeleri belirten XML dosyalarının listesini içerir.<br /><br /> Ayarlandığında, `InstalledAssemblyTables` listedeki derlemelerin önceki sürümleri XML'de listelenen yeni sürümlerle birleştirilir. Ayrıca, InGAC='true' ayarı olan derlemeler ön koşul olarak kabul edilir ve açıkça geçersiz kılınmadığı sürece CopyLocal='false' olarak ayarlanır.<br /><br /> Bir seçenek olarak, bu listedeki öğeler belirli bir `InstalledAssemblyTable` çerçeve dizini ile ilişkilendirmek için "FrameworkDirectory" meta verileri belirtebilir.  Ancak, Redist adı ile başlayan sürece bu ayar yoksayılır<br /><br /> "Microsoft-Windows-CLRCoreComp".<br /><br /> Yalnızca bir `TargetFrameworkDirectories` öğe varsa, bu listede "FrameworkDirectory" meta verilerinden yoksun olan öğeler, geçirilen benzersiz değere ayarlanmış gibi değerlendirilir.<br /><br /> için `TargetFrameworkDirectories`.|
|`LatestTargetFrameworkDirectories`|İsteğe bağlı `String[]` parametre.<br /><br /> Makinede hedeflenebilen en güncel çerçeve için redist listelerini içeren dizinlerin listesini belirtir. Bu ayarlanmazsa, belirli bir hedef çerçeve tanımlayıcısı için makineye yüklenen en yüksek çerçeve kullanılır.|
|`ProfileName`|İsteğe bağlı `String` parametre.<br /><br /> - Hedeflenecek çerçeve profilinin adını belirtir. Örneğin, İstemci, Web veya Ağ.|
|`RelatedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Başvuruyla aynı temel ada sahip XML ve *.pdb* dosyaları gibi ilgili dosyaları içerir.<br /><br /> Bu parametrede listelenen dosyalar isteğe bağlı olarak aşağıdaki öğe meta verilerini içerebilir:<br /><br /> -   `Primary`: `Boolean` değer. Eğer `true`, sonra dosya öğesi `Assemblies` parametre kullanılarak diziiçine geçirildi. Varsayılan değer. `false`<br />-   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıktı dizinine kopyalanıp kopyalanmayacağını gösterir.|
|`ResolvedDependencyFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Bağımlılıklara *giden n*th sıralı yolları içerir. Bu parametre, `ResolvedFiles` parametrede bulunan birinci sınıf birincil başvuruları içermez.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki madde meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıktı dizinine kopyalanıp kopyalanmayacağını gösterir.<br />-   `FusionName`: `String` değer. Bu bağımlılık için adı belirtir.<br />-   `ResolvedFrom`: `String` değer. Bu dosyanın çözümlendirilen gerçek arama yolunu belirtir.|
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Tam yollara çözülen tüm birincil başvuruların listesini içerir.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki madde meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıktı dizinine kopyalanıp kopyalanmayacağını gösterir.<br />-   `FusionName`: `String` değer. Bu bağımlılık için adı belirtir.<br />-   `ResolvedFrom`: `String` değer. Bu dosyanın çözümlendirilen gerçek arama yolunu belirtir.|
|`SatelliteFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Bulunan tüm uydu dosyalarını belirtir. Bu öğenin var olmasına neden olan başvuru veya bağımlılık CopyLocal=true ise bunlar CopyLocal=true olacaktır.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki madde meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıktı dizinine kopyalanıp kopyalanmayacağını gösterir. Bu değer, `true` bu öğenin var `CopyLocal` olmasına neden olan başvuru `true`veya bağımlılık.<br />-   `DestinationSubDirectory`: `String` değer. Bu öğeyi kopyalamak için göreli hedef dizinini belirtir.|
|`ScatterFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Verilen derlemelerden biriyle ilişkili dağılım dosyalarını içerir.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki madde meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıktı dizinine kopyalanıp kopyalanmayacağını gösterir.|
|`SearchPaths`|Gerekli `String[]` parametre.<br /><br /> Derlemeleri temsil eden diskteki dosyaları bulmak için aranan dizinleri veya özel konumları belirtir. Arama yollarının listelenme sırası önemlidir. Her derleme için, yolların listesi soldan sağa aranır. Derlemeyi temsil eden bir dosya bulunduğunda, bu arama durur ve bir sonraki derleme için arama başlar.<br /><br /> Bu parametre, aşağıdaki listeden dizin yolları veya özel edebi değerler olabilecek yarı sütunlu sınırlı bir değer listesini kabul eder:<br /><br /> -   `{HintPathFromItem}`: Görevin temel öğenin `HintPath` meta verilerini inceleyeceğini belirtir.<br />-   `{CandidateAssemblyFiles}`: Görevin `CandidateAssemblyFiles` parametreden geçen dosyaları inceleyeceğini belirtir.<br />-   `{Registry:`\<AssemblyFoldersBase>, \<RuntimeVersion \<>, AssemblyFoldersSonefix>`}`: Görevin kayıt defterinde belirtilen ek klasörlerde arama yapacağı belirtilir. \<AssemblyFoldersBase>, \<RuntimeVersion \<> ve AssemblyFoldersSonefix>, kayıt defteri konumunun aranması için belirli değerlerle değiştirilmelidir. Ortak hedeflerdeki varsayılan belirtim {Registry:$(FrameworkRegistryBase), $(TargetFrameworkVersion), $(AssemblyFoldersSuffix), $(AssemblyFoldersExConditions)}'dir.<br />-   `{AssemblyFolders}`: Görevin Visual Studio.NET 2003 bulgu-derlemeleri-kayıt defteri şeması kullanacağını belirtir.<br />-   `{GAC}`: Görevin Genel Montaj Önbelleğinde (GAC) aranacağını belirtir.<br />-   `{RawFileName}`: Görevin, öğenin `Include` değerini tam bir yol ve dosya adı olarak dikkate alacağı belirtilir.|
|`SerializationAssemblyFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> Bulunan tüm XML serileştirme derlemelerini içerir. Bu öğeler CopyLocal=true olarak işaretlenir ve yalnızca bu öğenin bulunmasına neden olan başvuru veya bağımlılık CopyLocal=true ise olur.<br /><br /> `Boolean` Meta data CopyLocal, verilen başvurunun çıktı dizinine kopyalanıp kopyalanmayacağını gösterir.|
|`Silent`|İsteğe bağlı `Boolean` parametre.<br /><br /> İleti `true`günlüğe kaydedilmezse. Varsayılan değer: `false`.|
|`StateFile`|İsteğe bağlı `String` parametre.<br /><br /> Ara yapı durumunun bu görev için nereye kaydedileceklerini belirten bir dosya adı belirtir.|
|`SuggestedRedirects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur çıktı parametresi.<br /><br /> `AutoUnify` Parametrenin değerine bakılmaksızın, her farklı çakışan derleme kimliği için bir öğe içerir. Bu, uygulama yapılandırma dosyasında uygun bir bağlayıcısı Olmayan her kültürü ve PKT'yi içerir.<br /><br /> Her öğe isteğe bağlı olarak aşağıdaki bilgileri içerir:<br /><br /> -   `Include`öznitelik: 0.0.0.0 Sürüm alan değeri ile derleme ailesinin tam adını içerir<br />-   `MaxVersion`madde meta verileri: Maksimum sürüm numarasını içerir.|
|`TargetedRuntimeVersion`|İsteğe bağlı `String` parametre.<br /><br /> Örneğin, 2.0.57027 veya v2.0.57027'yi hedeflemek için çalışma zamanı sürümünü belirtir.|
|`TargetFrameworkDirectories`|İsteğe bağlı `String[]` parametre.<br /><br /> Hedef çerçeve dizininin yolunu belirtir. Bu parametre, elde edilen öğeler için CopyLocal durumunu belirlemek için gereklidir.<br /><br /> Bu parametre belirtilmemişse, kaynak `true` `Private` `true` öğesinde açıkça bir meta veri değeri olmadığı sürece, ortaya çıkan hiçbir öğenin CopyLocal değeri olmaz.|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametre.<br /><br /> Varsa, izlemek için TargetFrameworkMoniker. Bu günlüğe kaydetme için kullanılır.|
|`TargetFrameworkMonikerDisplayName`|İsteğe bağlı `String` parametre.<br /><br /> Varsa izlenecek TargetFrameworkMoniker'ın ekran adı. Bu günlüğe kaydetme için kullanılır.|
|`TargetFrameworkSubsets`|İsteğe bağlı `String[]` parametre.<br /><br /> Hedef çerçeve dizinlerinde aranacak hedef çerçeve alt kümesi adlarının listesini içerir.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> Proje hedef çerçeve sürümü. Varsayılan değer boştur, bu da hedef çerçeveye dayalı başvurular için filtreleme olmadığı anlamına gelir.|
|`TargetProcessorArchitecture`|İsteğe bağlı `String` parametre.<br /><br /> Tercih edilen hedef işlemci mimarisi. Genel Derleme Önbelleği (GAC) başvurularını çözmek için kullanılır.<br /><br /> Bu parametre `x86`, `IA64`veya `AMD64`.<br /><br /> Bu parametre yoksa, görev ilk olarak şu anda çalışan işlemin mimarisiyle eşleşen derlemeleri dikkate alır. Derleme bulunamazsa, görev GAC'de değeri olan `ProcessorArchitecture` `MSIL` veya değeri `ProcessorArchitecture` olmayan derlemeleri dikkate alır.|

## <a name="warnings"></a>Uyarılar

 Aşağıdaki uyarılar günlüğe kaydedilir:

- `ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects`

- `ResolveAssemblyReference.SuggestedRedirects`

- `ResolveAssemblyReference.FoundConflicts`

- `ResolveAssemblyReference.AssemblyFoldersExSearchLocations`

- `ResolveAssemblyReference.UnifiedPrimaryReference`

- `ResolveAssemblyReference.PrimaryReference`

- `ResolveAssemblyReference.UnifiedDependency`

- `ResolveAssemblyReference.UnificationByAutoUnify`

- `ResolveAssemblyReference.UnificationByAppConfig`

- `ResolveAssemblyReference.UnificationByFrameworkRetarget`

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
