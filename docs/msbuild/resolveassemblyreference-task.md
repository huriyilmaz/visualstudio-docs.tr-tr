---
title: ResolveAssemblyReference görevi | Microsoft Docs
description: MSBuild, belirtilen derlemelere bağlı olan tüm derlemeleri belirlemede, resolveassemblyreference görevini nasıl kullandığını öğrenin.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d180c8cea42076e2ca4a39a57dbabe6ebbf4b1c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108414"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference görevi

İkinci ve daha sıralı bağımlılıklar dahil olmak üzere belirtilen derlemelere bağlı tüm derlemeleri belirler `n` .

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `ResolveAssemblyReference` .

|Parametre|Açıklama|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|İsteğe bağlı `String[]` parametre.<br /><br /> Başvurular çözümlenirken kullanılacak derleme dosya adı uzantıları. Varsayılan dosya adı uzantıları *.exe* ve *.dll*.|
|`AllowedRelatedFileExtensions`|İsteğe bağlı `String[]` parametre.<br /><br /> Birbirleriyle ilgili dosyaları aramak için kullanılacak dosya adı uzantıları. Varsayılan uzantılar *. pdb* ve *.xml*.|
|`AppConfigFile`|İsteğe bağlı `String` parametre.<br /><br /> BindingRedirect eşlemelerini ayrıştırmak ve ayıklamak için içinden bir *app.config* dosyası belirtir. Bu parametre belirtilmişse `AutoUnify` parametrenin olması gerekir `false` .|
|`Assemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Tam yolların ve bağımlılıkların tanımlanması gereken öğeleri belirtir. Bu öğeler "sistem" gibi basit adlara veya "sistem, sürüm = 2.0.3500.0, Culture = neutral, PublicKeyToken = b77a5c561934e089" gibi tanımlayıcı adlara sahip olabilir.<br /><br /> Bu parametreye geçirilen öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerine sahip olabilir:<br /><br /> -   `Private`: `Boolean` değer. Varsa `true` , öğe yerel olarak kopyalanır. `true` varsayılan değerdir.<br />-   `HintPath`: `String` değer. Başvuru olarak kullanılacak yolu ve dosya adını belirtir. Bu meta veriler, parametrede {HintPathFromItem} belirtildiğinde kullanılır `SearchPaths` . Varsayılan değer boş bir dizedir.<br />-   `SpecificVersion`: `Boolean` değer. İse `true` , özniteliğinde belirtilen tam adın `Include` eşleşmesi gerekir. Varsa `false` , aynı basit ada sahip herhangi bir derleme çalışacaktır. `SpecificVersion`Belirtilmemişse, görev `Include` öğenin özniteliğinde değeri inceler. Öznitelik basit bir ad ise, olduğu gibi davranır `SpecificVersion` `false` . Öznitelik bir tanımlayıcı ad ise, olduğu gibi davranır `SpecificVersion` `true` .<br />     Bir başvuru öğesi türü ile kullanıldığında, `Include` özniteliğin çözümlenecek derlemenin tam Fusion adı olması gerekir. Derleme yalnızca Fusion özniteliğiyle tam olarak eşleşiyorsa çözümlenir `Include` .<br />     bir proje bir .NET Framework sürümünü hedefliyorsa ve daha yüksek bir .NET Framework sürümü için derlenmiş bir derlemeye başvuruyorsa, başvuru yalnızca `SpecificVersion` olarak ayarlandıysa çözümlenir `true` .<br />     Bir proje bir profili hedefliyorsa ve profilde olmayan bir derlemeye başvurduğunda, başvuru yalnızca `SpecificVersion` olarak ayarlandıysa çözümlenir `true` .<br />-   `ExecutableExtension`: `String` değer. Mevcut olduğunda, çözümlenen derlemenin bu uzantıya sahip olması gerekir. Olmadığında, *.dll* ilk olarak değerlendirilir ve ardından *.exe*, denetlenen her dizin için.<br />-   `SubType`: `String` değer. Yalnızca boş alt tür meta verilerine sahip öğeler, tam derleme yollarına çözümlenir. Boş olmayan SubType meta verilerine sahip öğeler yok sayılır.<br />-   `AssemblyFolderKey`: `String` değer. Bu meta veriler eski amaçlar için desteklenir. **\\ \<VendorFolder>** `Assemblies` Derleme başvurularını çözümlemek için kullanması gereken HKLM gibi Kullanıcı tanımlı bir kayıt defteri anahtarını belirtir.|
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
|`FullFrameworkAssemblyTables`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bir redist listesini belirli bir çerçeve diziniyle ilişkilendirmek için "FrameworkDirectory" meta verilerine sahip öğeleri belirtir. İlişkililik yoksa bir hata günlüğe kaydedilir. FrameworkDirectory ayarlanmazsa çözüm derleme başvurusu (RAR) mantığı hedef çerçeve dizinini kullanır.|
|`FullFrameworkFolders`|İsteğe <xref:System.String?displayProperty=fullName> `[]` bağlı parametre.<br /><br /> RedistList dizini içeren klasörleri belirtir. Bu dizin, belirli bir istemci profili için tam çerçeveyi temsil eder; örneğin, *%programfiles%\reference assemblies\microsoft\framework\v4.0*.|
|`FullTargetFrameworkSubsetNames`|İsteğe `String[]` bağlı parametre.<br /><br /> Hedef çerçeve alt kümesi adlarının listesini içerir. Listede yer alan bir alt küme adı name özelliğinde bir adla eşlese, sistem derleme zamanında bu hedef çerçeve alt `TargetFrameworkSubset` kümesini dışlar.|
|`IgnoreDefaultInstalledAssemblyTables`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, görev altında \RedistList dizininde bulunan ek yüklü derleme tablolarını `true` *("Redist* Listeleri") arar ve `TargetFrameworkDirectories` kullanır. Varsayılan değer: `false.`|
|`IgnoreDefaultInstalledAssemblySubsetTables`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` görev altında *\SubsetList* dizininde bulunan ek yüklü derleme alt küme tablolarını ("Alt Küme Listeleri") arar ve `TargetFrameworkDirectories` kullanır. Varsayılan değer: `false.`|
|`InstalledAssemblySubsetTables`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Hedef alt kümede olması beklenen derlemeleri belirten XML dosyalarının listesini içerir.<br /><br /> Seçenek olarak, bu listede yer alan öğeler bir `InstalledAssemblySubsetTable`<br /><br /> belirli bir çerçeve dizinine sahip.<br /><br /> Yalnızca bir öğe varsa, bu listede "FrameworkDirectory" meta verisi olmayan öğeler, öğesine geçirilen benzersiz değere ayarlanmış `TargetFrameworkDirectories` gibi kabul `TargetFrameworkDirectories` edilir.|
|`InstalledAssemblyTables`|İsteğe `String` bağlı parametre.<br /><br /> Hedef bilgisayarda yüklü olması beklenen derlemeleri belirten XML dosyalarının listesini içerir.<br /><br /> Ayar `InstalledAssemblyTables` olduğunda, listede derlemelerin önceki sürümleri XML'de listelenen daha yeni sürümlerle birleştirilir. Ayrıca, InGAC='true' ayarına sahip derlemeler önkoşul olarak kabul edilir ve açıkça geçersiz kılınmadıkça CopyLocal='false' olarak ayarlanır.<br /><br /> Seçenek olarak, bu listede yer alan öğeler belirli bir çerçeve diziniyle ilişkilendirmek için "FrameworkDirectory" `InstalledAssemblyTable` meta verilerini belirtebilirsiniz.  Ancak, Redist adı ile başlayana kadar bu ayar yoksayılır<br /><br /> "Microsoft-Windows-CLRCoreComp".<br /><br /> Yalnızca bir öğe varsa, bu listede "FrameworkDirectory" meta verisi olmayan öğeler geçirilen benzersiz değere ayarlanmış gibi `TargetFrameworkDirectories` kabul edilir<br /><br /> için `TargetFrameworkDirectories` .|
|`LatestTargetFrameworkDirectories`|İsteğe `String[]` bağlı parametre.<br /><br /> Makinede hedeflen en güncel çerçeve için redist listelerini içeren dizinlerin listesini belirtir. Bu ayarlanmazsa, makinede yüklü olan en yüksek çerçeve, verilen bir hedef çerçeve tanımlayıcısı için kullanılır.|
|`ProfileName`|İsteğe `String` bağlı parametre.<br /><br /> - Hedeflen çerçeve profilinin adını belirtir. Örneğin, İstemci, Web veya Ağ.|
|`RelatedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Başvuruyla aynı temel adı olan XML ve *.pdb* dosyaları gibi ilgili dosyaları içerir.<br /><br /> Bu parametrede listelenen dosyalar isteğe bağlı olarak aşağıdaki öğe meta verilerini içerebilir:<br /><br /> -   `Primary`: `Boolean` değeri. ise, `true` dosya öğesi parametresi kullanılarak diziye `Assemblies` geçirildi. Varsayılan değer `false` olarak belirlenmiştir.<br />-   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.|
|`ResolvedDependencyFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Bağımlılıkların *n.* sıra yollarını içerir. Bu parametre, parametresinde yer alan ilk sipariş birincil başvurularını `ResolvedFiles` içermez.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.<br />-   `FusionName`: `String` değeri. Bu bağımlılığın adını belirtir.<br />-   `ResolvedFrom`: `String` değeri. Bu dosyanın çözümlenmiş olduğu değişmez arama yolunu belirtir.|
|`ResolvedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Tam yollara çözümlenen tüm birincil başvuruların listesini içerir.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.<br />-   `FusionName`: `String` değeri. Bu bağımlılığın adını belirtir.<br />-   `ResolvedFrom`: `String` değeri. Bu dosyanın çözümlenmiş olduğu değişmez arama yolunu belirtir.|
|`SatelliteFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Bulunan tüm uydu dosyalarını belirtir. CopyLocal=true ise, bu öğenin varolmalarına neden olan başvuru veya bağımlılık CopyLocal=true olur.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir. Bu değer, `true` bu öğenin varolmalarına neden olan başvuru veya bağımlılığın değerine sahip `CopyLocal` `true` olmasıdır.<br />-   `DestinationSubDirectory`: `String` değeri. Bu öğeyi kopyalamak için göreli hedef dizini belirtir.|
|`ScatterFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Verilen derlemelerden biri ile ilişkili dağılım dosyalarını içerir.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.|
|`SearchPaths`|Gerekli `String[]` parametre.<br /><br /> Derlemeleri temsil eden diskte dosyaları bulmak için aranan dizinleri veya özel konumları belirtir. Arama yollarının liste sırası önemlidir. Her derleme için yol listesi soldan sağa aranır. Derlemeyi temsil eden bir dosya bulunursa, bu arama durur ve sonraki derleme için arama başlar.<br /><br /> Bu parametre, aşağıdaki listeden dizin yolları veya özel değişmez değerler olan noktalı virgülle ayrılmış değerler listesini kabul eder:<br /><br /> -   `{HintPathFromItem}`: Görevin temel öğenin meta `HintPath` verilerini inceleyeceklerini belirtir.<br />-   `{CandidateAssemblyFiles}`: Görevin parametresi aracılığıyla geçirilen dosyaları inceleyeceklerini `CandidateAssemblyFiles` belirtir.<br />-   `{Registry:`\<AssemblyFoldersBase>, \<RuntimeVersion> , : Görevin kayıt defterinde belirtilen ek \<AssemblyFoldersSuffix> `}` klasörlerde aranacak olduğunu belirtir. \<AssemblyFoldersBase>, \<RuntimeVersion> , \<AssemblyFoldersSuffix> ve, aranacak kayıt defteri konumu için belirli değerlerle değiştir değiştiri. Ortak hedeflerde varsayılan belirtim şu şekildedir: {Registry:$(FrameworkRegistryBase), $(TargetFrameworkVersion), $(AssemblyFoldersSuffix), $(AssemblyFoldersExConditions)}.<br />-   `{AssemblyFolders}`: Görevin Visual Studio.NET 2003 finding-assemblies-from-registry şemasını kullanmayacaklarını belirtir.<br />-   `{GAC}`: Görevin Genel Derleme Önbelleği'nde (GAC) aranacak olduğunu belirtir.<br />-   `{RawFileName}`: Görevin öğenin değerini tam `Include` yol ve dosya adı olarak değerlendireceklerini belirtir.|
|`SerializationAssemblyFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Bulunan tüm XML serileştirme derlemelerini içerir. Bu öğeler copyLocal=true ise ve yalnızca bu öğenin varolmalarına neden olan başvuru veya bağımlılık CopyLocal=true ise işaretlenir.<br /><br /> `Boolean`CopyLocal meta verileri verilen başvuruya çıkış dizinine kopyalayıp kopyalanmay gerektiğini gösterir.|
|`Silent`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` hiçbir ileti günlüğe kaydedilmez. `false` varsayılan değerdir.|
|`StateFile`|İsteğe `String` bağlı parametre.<br /><br /> Bu görev için ara derleme durumunun kaydedileceği yeri gösteren bir dosya adı belirtir.|
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
