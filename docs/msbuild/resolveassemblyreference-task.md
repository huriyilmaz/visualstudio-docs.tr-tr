---
title: ResolveAssemblyReference görevi | Microsoft Docs
description: MSBuild 'in, belirtilen derlemelere bağlı olan tüm derlemeleri belirlemede ResolveAssemblyReference görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bccdc376079c4d9e0efb2a2724831e0fd2d0ae14
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048665"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference görevi

İkinci ve daha sıralı bağımlılıklar dahil olmak üzere belirtilen derlemelere bağlı tüm derlemeleri belirler `n` .

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `ResolveAssemblyReference` .

|Parametre|Açıklama|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|İsteğe bağlı `String[]` parametre.<br /><br /> Başvurular çözümlenirken kullanılacak derleme dosya adı uzantıları. Varsayılan dosya adı uzantıları *. exe* ve *. dll* ' dir.|
|`AllowedRelatedFileExtensions`|İsteğe bağlı `String[]` parametre.<br /><br /> Birbirleriyle ilgili dosyaları aramak için kullanılacak dosya adı uzantıları. Varsayılan uzantılar *. pdb* ve *. xml* ' dir.|
|`AppConfigFile`|İsteğe bağlı `String` parametre.<br /><br /> BindingRedirect eşlemelerini ayrıştırmak ve ayıklamak için içinden bir *app.config* dosyası belirtir. Bu parametre belirtilmişse `AutoUnify` parametrenin olması gerekir `false` .|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Tam yolların ve bağımlılıkların tanımlanması gereken öğeleri belirtir. Bu öğeler "sistem" gibi basit adlara veya "sistem, sürüm = 2.0.3500.0, Culture = neutral, PublicKeyToken = b77a5c561934e089" gibi tanımlayıcı adlara sahip olabilir.<br /><br /> Bu parametreye geçirilen öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerine sahip olabilir:<br /><br /> -   `Private`: `Boolean` değer. Varsa `true` , öğe yerel olarak kopyalanır. `true` varsayılan değerdir.<br />-   `HintPath`: `String` değer. Başvuru olarak kullanılacak yolu ve dosya adını belirtir. Bu meta veriler, parametrede {HintPathFromItem} belirtildiğinde kullanılır `SearchPaths` . Varsayılan değer boş bir dizedir.<br />-   `SpecificVersion`: `Boolean` değer. İse `true` , özniteliğinde belirtilen tam adın `Include` eşleşmesi gerekir. Varsa `false` , aynı basit ada sahip herhangi bir derleme çalışacaktır. `SpecificVersion`Belirtilmemişse, görev `Include` öğenin özniteliğinde değeri inceler. Öznitelik basit bir ad ise, olduğu gibi davranır `SpecificVersion` `false` . Öznitelik bir tanımlayıcı ad ise, olduğu gibi davranır `SpecificVersion` `true` .<br />     Bir başvuru öğesi türü ile kullanıldığında, `Include` özniteliğin çözümlenecek derlemenin tam Fusion adı olması gerekir. Derleme yalnızca Fusion özniteliğiyle tam olarak eşleşiyorsa çözümlenir `Include` .<br />     Bir proje bir .NET Framework sürümünü hedefliyorsa ve daha yüksek bir .NET Framework sürümü için derlenmiş bir derlemeye başvuruyorsa, başvuru yalnızca `SpecificVersion` olarak ayarlandıysa çözümlenir `true` .<br />     Bir proje bir profili hedefliyorsa ve profilde olmayan bir derlemeye başvurduğunda, başvuru yalnızca `SpecificVersion` olarak ayarlandıysa çözümlenir `true` .<br />-   `ExecutableExtension`: `String` değer. Mevcut olduğunda, çözümlenen derlemenin bu uzantıya sahip olması gerekir. Olmadığında, her bir denetlenen dizin için. *DLL* önce *. exe* olarak değerlendirilir.<br />-   `SubType`: `String` değer. Yalnızca boş alt tür meta verilerine sahip öğeler, tam derleme yollarına çözümlenir. Boş olmayan SubType meta verilerine sahip öğeler yok sayılır.<br />-   `AssemblyFolderKey`: `String` değer. Bu meta veriler eski amaçlar için desteklenir. **\\ \<VendorFolder>** `Assemblies` Derleme başvurularını çözümlemek için kullanması gereken HKLM gibi Kullanıcı tanımlı bir kayıt defteri anahtarını belirtir.|
|`AssemblyFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bağımlılıklarını bulmak için tam nitelikli derlemelerin bir listesini belirtir.<br /><br /> Bu parametreye geçirilen öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerine sahip olabilir:<br /><br /> -   `Private`: isteğe bağlı bir `Boolean` değer. True ise, öğe yerel olarak kopyalanır.<br />-   `FusionName`: isteğe bağlı `String` meta veriler. Bu öğe için basit veya tanımlayıcı adı belirtir. Bu öznitelik varsa, adı almak için derleme dosyası açılmadığından zaman tasarrufu yapabilirsiniz.|
|`AutoUnify`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre, normal bir *App.Config* dosyasına sahip olmayan dll 'ler gibi derlemeler oluşturmak için kullanılır.<br /><br /> Ne zaman `true` elde edilen bağımlılık grafiği, AppConfigFile parametresine geçirilmiş bir *App.Config* dosyası gibi otomatik olarak değerlendirilir. Bu sanal *App.Config* dosyası, en yüksek sürüm derlemesi seçili olacak şekilde, çakışan her bir derleme kümesi Için bir bindingRedirect girişi içerir. Bunun sonucunda, çakışan derlemeler hakkında hiçbir uyarı olmamasının nedeni, her çakışma çözümlenmeyecektir.<br /><br /> Ne zaman `true` , her ayrı yeniden eşleme, eski ve yeni sürümleri gösteren ve olan yüksek öncelikli bir açıklamaya neden `AutoUnify` olur `true` .<br /><br /> Ne zaman `true` , AppConfigFile parametresi boş olmalıdır.<br /><br /> Ne zaman `false` , hiçbir derleme sürümü yeniden eşlemesi otomatik olarak gerçekleşmez. Bir derlemenin iki sürümü mevcut olduğunda bir uyarı verilir.<br /><br /> `false`Aynı derlemenin farklı sürümleri arasındaki her bir ayrı çakışma, yüksek öncelikli bir açıklamaya neden olur. Bu açıklamaların ardından tek bir uyarı gelir. Uyarı benzersiz bir hata koduna sahiptir ve "başvuru ve bağımlı derlemelerin farklı sürümleri arasında bulunan çakışmaları" okuyan metni içerir.<br /><br /> `false` varsayılan değerdir.|
|`CandidateAssemblyFiles`|İsteğe bağlı `String[]` parametre.<br /><br /> Arama ve çözümleme işlemi için kullanılacak derlemelerin bir listesini belirtir. Bu parametreye geçirilen değerler mutlak dosya adları veya proje göreli dosya adları olmalıdır.<br /><br /> Bu listedeki derlemeler, `SearchPaths` dikkate alınması gereken yollardan biri olarak parametre {CandidateAssemblyFiles} içerdiğinde göz önünde bulundurulacaktır.|
|`CopyLocalDependenciesWhenParentReferenceInGac`|İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> Doğru ise, bir bağımlılığın yerel olarak kopyalanıp kopyalanmayacağını anlamak için yapılan denetimlerden biri, proje dosyasındaki üst başvurunun özel meta veri kümesine sahip olup olmadığını görebilmelidir. Ayarlanırsa, özel değer bir bağımlılık olarak kullanılır.<br /><br /> Meta veriler ayarlanmamışsa, bağımlılık üst başvuru ile aynı denetimlerden geçer. Bu denetimlerden biri başvurunun GAC içinde olup olmadığını gördir. Bir başvuru GAC 'deyse, hedef makinede GAC 'de olduğu varsayıldığından yerel olarak kopyalanmaz. Bu yalnızca belirli bir başvuruya uygulanır ve bağımlılıkları değildir.<br /><br /> Örneğin, GAC 'deki proje dosyasındaki bir başvuru yerel olarak kopyalanmaz, ancak bu GAC 'de olmadıkları için bağımlılıkları yerel olarak kopyalanır.<br /><br /> Yanlış ise, proje dosyası başvuruları GAC içinde olup olmadığını görmek için denetlenir ve uygun şekilde yerel olarak kopyalanır.<br /><br /> Bağımlılıklar GAC içinde olup olmadığını ve ayrıca proje dosyasındaki üst başvurunun GAC 'de olup olmadığını görmek için denetlenir.<br /><br /> Proje dosyasındaki üst başvuru GAC 'deyse, bağımlılık yerel olarak kopyalanmaz.<br /><br /> Bu parametrenin doğru veya yanlış olduğunu, birden fazla üst başvuru varsa ve bunlar GAC 'de yoksa, hepsi yerel olarak kopyalanır.|
|`CopyLocalFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> ,,, `ResolvedFiles` `ResolvedDependencyFiles` `RelatedFiles` `SatelliteFiles` Ve `ScatterFiles` `CopyLocal` değerlerini içeren öğe meta verileri olan parametrelerde `true` her dosyayı döndürür.|
|`FilesWritten`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Diske yazılan öğeleri içerir.|
|`FindDependencies`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , bağımlılıklar bulunur. Aksi takdirde, yalnızca birincil başvurular bulunur. `true` varsayılan değerdir.|
|`FindRelatedFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true` *. Pdb* dosyaları ve *XML* dosyaları gibi ilgili dosyalar bulunur. `true` varsayılan değerdir.|
|`FindSatellites`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , uydu derlemeleri bulunacaktır. Varsayılan değer: `true.`|
|`FindSerializationAssemblies`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Daha sonra görev, serileştirme derlemeleri arar. `true` varsayılan değerdir.|
|`FullFrameworkAssemblyTables`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir Redist listesini belirli bir çerçeve diziniyle ilişkilendirmek için "FrameworkDirectory" meta verileri olan öğeleri belirtir. İlişkilendirme yapılmadıysa bir hata günlüğe kaydedilir. Bir FrameworkDirectory ayarlanmamışsa, derleme başvurusunu çözümle (RAR) mantığı hedef Framework dizinini kullanır.|
|`FullFrameworkFolders`|İsteğe bağlı <xref:System.String?displayProperty=fullName> `[]` parametre.<br /><br /> RedistList dizinini içeren klasörleri belirtir. Bu dizin, belirli bir istemci profili için tam çerçeveyi temsil eder, örneğin, *%ProgramFiles%\Reference, lıes\microsoft\framework\v4.0* .|
|`FullTargetFrameworkSubsetNames`|İsteğe bağlı `String[]` parametre.<br /><br /> Hedef çerçeve alt küme adlarının bir listesini içerir. Listedeki bir alt küme adı, `TargetFrameworkSubset` Name özelliğinden biriyle eşleşiyorsa, sistem söz konusu hedef Framework alt kümesini derleme zamanında dışlar.|
|`IgnoreDefaultInstalledAssemblyTables`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Daha sonra görev, altındaki *\Redistlist* dizininde bulunan ek yüklü derleme tablolarını (veya "yeniden dağıtım listeleri") kullanır `TargetFrameworkDirectories` . Varsayılan değer: `false.`|
|`IgnoreDefaultInstalledAssemblySubsetTables`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Daha sonra görev, altındaki *\Subsetlist* dizininde bulunan ek yüklü derleme alt kümesi tablolarını (veya "alt küme listeleri") kullanır `TargetFrameworkDirectories` . Varsayılan değer: `false.`|
|`InstalledAssemblySubsetTables`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Hedef alt kümede olması beklenen derlemeleri belirten XML dosyalarının bir listesini içerir.<br /><br /> Bir seçenek olarak, bu listedeki öğeler, bir ile ilişkilendirilecek "FrameworkDirectory" meta verilerini belirtebilir `InstalledAssemblySubsetTable`<br /><br /> belirli bir çerçeve diziniyle.<br /><br /> Yalnızca bir `TargetFrameworkDirectories` öğe varsa, bu listedeki "FrameworkDirectory" meta verileri olmayan her türlü öğe, geçirilen benzersiz değere ayarlansa da kabul edilir `TargetFrameworkDirectories` .|
|`InstalledAssemblyTables`|İsteğe bağlı `String` parametre.<br /><br /> Hedef bilgisayarda yüklü olması beklenen derlemeleri belirten XML dosyalarının bir listesini içerir.<br /><br /> Ayarlandığında `InstalledAssemblyTables` , listedeki derlemelerin önceki sürümleri, XML 'de listelenen yeni sürümlere birleştirilir. Ayrıca, bir InGAC = ' true ' ayarına sahip derlemeler önkoşulları kabul edilir ve açıkça geçersiz kılınmadıkça CopyLocal = ' false ' olarak ayarlanır.<br /><br /> Bir seçenek olarak, bu listedeki öğeler belirli bir çerçeve diziniyle ilişkilendirilecek "FrameworkDirectory" meta verilerini belirtebilir `InstalledAssemblyTable` .  Ancak, yeniden dağıtım adı ile başlamadıkça Bu ayar yok sayılır<br /><br /> "Microsoft-Windows-CLRCoreComp".<br /><br /> Yalnızca bir `TargetFrameworkDirectories` öğe varsa, bu listedeki "FrameworkDirectory" meta verileri olmayan her türlü öğe, geçirilen benzersiz değere ayarlanmış gibi değerlendirilir<br /><br /> `TargetFrameworkDirectories`.|
|`LatestTargetFrameworkDirectories`|İsteğe bağlı `String[]` parametre.<br /><br /> Makineye hedeflenebilir en güncel Framework için yeniden dağıtım listelerini içeren dizinlerin listesini belirtir. Bu ayarlanmamışsa, belirli bir hedef çerçeve tanımlayıcısı için makinede yüklü en yüksek çerçeve kullanılır.|
|`ProfileName`|İsteğe bağlı `String` parametre.<br /><br /> -Hedeflenen çerçeve profilinin adını belirtir. Örneğin, Istemci, Web veya ağ.|
|`RelatedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Başvuru ile aynı temel ada sahip XML ve *. pdb* dosyaları gibi ilgili dosyaları içerir.<br /><br /> Bu parametrede listelenen dosyalar isteğe bağlı olarak aşağıdaki öğe meta verilerini içerebilir:<br /><br /> -   `Primary`: `Boolean` değer. İse `true` , dosya öğesi parametresi kullanılarak diziye geçirilir `Assemblies` . Varsayılan değer `false` olarak belirlenmiştir.<br />-   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıkış dizinine kopyalanıp kopyalanmayacağını belirtir.|
|`ResolvedDependencyFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Bağımlılıklara yönelik olan *n* . sıralama yollarını içerir. Bu parametre, parametresinde yer alan ilk sıra birincil başvurularını içermez `ResolvedFiles` .<br /><br /> Bu parametresindeki öğeler, isteğe bağlı olarak şu öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıkış dizinine kopyalanıp kopyalanmayacağını belirtir.<br />-   `FusionName`: `String` değer. Bu bağımlılığın adını belirtir.<br />-   `ResolvedFrom`: `String` değer. Bu dosyanın çözümlendiği sabit değer arama yolunu belirtir.|
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Tam yollara çözümlenen tüm birincil başvuruların bir listesini içerir.<br /><br /> Bu parametresindeki öğeler, isteğe bağlı olarak şu öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıkış dizinine kopyalanıp kopyalanmayacağını belirtir.<br />-   `FusionName`: `String` değer. Bu bağımlılığın adını belirtir.<br />-   `ResolvedFrom`: `String` değer. Bu dosyanın çözümlendiği sabit değer arama yolunu belirtir.|
|`SatelliteFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Bulunan herhangi bir uydu dosyasını belirtir. Bunlar CopyLocal = true olacaktır. bu öğeye neden olan başvuru veya bağımlılık CopyLocal = true ise geçerlidir.<br /><br /> Bu parametresindeki öğeler, isteğe bağlı olarak şu öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıkış dizinine kopyalanıp kopyalanmayacağını belirtir. Bu değer, `true` Bu öğenin var olmasına neden olan başvurunun veya bağımlılığın `CopyLocal` değeri varsa `true` .<br />-   `DestinationSubDirectory`: `String` değer. Bu öğenin kopyalanacağı göreli hedef dizini belirtir.|
|`ScatterFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Verilen derlemelerden biriyle ilişkili dağılım dosyalarını içerir.<br /><br /> Bu parametresindeki öğeler, isteğe bağlı olarak şu öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değer. Verilen başvurunun çıkış dizinine kopyalanıp kopyalanmayacağını belirtir.|
|`SearchPaths`|Gerekli `String[]` parametre.<br /><br /> Derlemeleri temsil eden diskte dosyaları bulmak için aranan dizinleri veya özel konumları belirtir. Arama yollarının listelenme sırası önemlidir. Her derleme için, yolların listesi soldan sağa aranır. Derlemeyi temsil eden bir dosya bulunduğunda bu arama duraklar ve sonraki derleme için arama başlar.<br /><br /> Bu parametre, aşağıdaki listeden dizin yolları veya özel değişmez değerler olabilecek değerlerin noktalı virgülle ayrılmış bir listesini kabul eder:<br /><br /> -   `{HintPathFromItem}`: Görevin `HintPath` temel öğenin meta verilerini inceleyeceği belirtir.<br />-   `{CandidateAssemblyFiles}`: Görevin, parametre aracılığıyla geçirilen dosyaları inceleyeceği belirtir `CandidateAssemblyFiles` .<br />-   `{Registry:`\<AssemblyFoldersBase>, \<RuntimeVersion> , \<AssemblyFoldersSuffix> `}` : Görevin kayıt defterinde belirtilen ek klasörlerde arama olacağını belirtir. \<AssemblyFoldersBase>, \<RuntimeVersion> ve, \<AssemblyFoldersSuffix> kayıt defteri konumunun aranacağı belirli değerlerle değiştirilmelidir. Ortak hedeflerde varsayılan belirtim {Registry: $ (FrameworkRegistryBase), $ (TargetFrameworkVersion), $ (AssemblyFoldersSuffix), $ (AssemblyFoldersExConditions)}.<br />-   `{AssemblyFolders}`: Görevin, Visual Studio.NET 2003 bulma-derleme-kayıt defteri düzenini kullanılacağını belirtir.<br />-   `{GAC}`: Genel derleme önbelleğinde (GAC) arama yapılacak görevi belirtir.<br />-   `{RawFileName}`: Görevin, `Include` öğenin değerini tam yol ve dosya adı olacak şekilde kabul edecek şekilde belirtir.|
|`SerializationAssemblyFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Bulunan tüm XML serileştirme derlemelerini içerir. Bu öğeler CopyLocal = true olarak işaretlenir ve yalnızca bu öğeye neden olan başvuru ya da bağımlılık CopyLocal = true ise geçerlidir.<br /><br /> `Boolean`Meta veri CopyLocal, belirtilen başvurunun çıkış dizinine kopyalanıp kopyalanmayacağını belirtir.|
|`Silent`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , hiçbir ileti günlüğe kaydedilmez. `false` varsayılan değerdir.|
|`StateFile`|İsteğe bağlı `String` parametre.<br /><br /> Bu görev için ara derleme durumunun kaydedileceği yeri gösteren bir dosya adı belirtir.|
|`SuggestedRedirects`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur çıkış parametresi.<br /><br /> Parametrenin değerinden bağımsız olarak, her ayrı çakışan derleme kimliği için bir öğe içerir `AutoUnify` . Bu, uygulama yapılandırma dosyasında uygun bir bindingRedirect girişi olmayan bulunan her kültür ve PKT 'yi içerir.<br /><br /> Her öğe isteğe bağlı olarak aşağıdaki bilgileri içerir:<br /><br /> -   `Include` öznitelik: sürüm alanı değeri 0.0.0.0 olan derleme ailesinin tam adını Içerir<br />-   `MaxVersion` öğe meta verileri: en yüksek sürüm numarasını Içerir.|
|`TargetedRuntimeVersion`|İsteğe bağlı `String` parametre.<br /><br /> Hedeflenecek çalışma zamanı sürümünü belirtir, örneğin, 2.0.57027 veya v 2.0.57027.|
|`TargetFrameworkDirectories`|İsteğe bağlı `String[]` parametre.<br /><br /> Hedef çerçeve dizininin yolunu belirtir. Bu parametre, sonuçta elde edilen öğelerin CopyLocal durumunu tespit etmek için gereklidir.<br /><br /> Bu parametre belirtilmemişse, hiçbir sonuç öğesi, `true` `Private` kendi kaynak öğelerinde meta veri değerine sahip olmadıkları müddetçe bir CopyLocal değerine sahip olmaz `true` .|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametre.<br /><br /> Varsa, izlenecek Targetframeworktakma adı. Bu günlüğe kaydetme için kullanılır.|
|`TargetFrameworkMonikerDisplayName`|İsteğe bağlı `String` parametre.<br /><br /> İzlemek için Targetframeworkbilinen adının görünen adı (varsa). Bu günlüğe kaydetme için kullanılır.|
|`TargetFrameworkSubsets`|İsteğe bağlı `String[]` parametre.<br /><br /> Hedef çerçeve dizinlerinde aranacak hedef çerçeve alt kümesi adlarının listesini içerir.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> Projenin hedef Framework sürümü. Varsayılan değer boştur; bu, hedef çerçeveye dayalı olarak başvurular için filtreleme olmadığı anlamına gelir.|
|`TargetProcessorArchitecture`|İsteğe bağlı `String` parametre.<br /><br /> Tercih edilen hedef işlemci mimarisi. Genel bütünleştirilmiş kod önbelleği (GAC) başvurularını çözümlemek için kullanılır.<br /><br /> Bu parametre,, veya değerine sahip `x86` olabilir `IA64` `AMD64` .<br /><br /> Bu parametre yoksa, görev önce çalışmakta olan işlemin mimarisiyle eşleşen derlemeleri kabul eder. Hiçbir derleme bulunamazsa, görev GAC 'de, değeri olmayan `ProcessorArchitecture` `MSIL` veya değer içermeyen derlemeleri kabul eder `ProcessorArchitecture` .|

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

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
