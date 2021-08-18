---
title: ResolveAssemblyReference Görev | Microsoft Docs
description: Belirtilen derlemelere MSBuild tüm derlemeleri belirlemek için ResolveAssemblyReference görevini nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 2164b29d221e838c54a539f4f3d965b89e5291835007b530317829af355826a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334087"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference görevi

İkinci ve sıra bağımlılıkları da dahil olmak üzere belirtilen derlemelere bağımlı `n` olan tüm derlemeleri belirler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `ResolveAssemblyReference` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|İsteğe `String[]` bağlı parametre.<br /><br /> Başvuruları çözümlerken kullanmak üzere derleme dosya adı uzantıları. Varsayılan dosya adı uzantıları.exe *ve* *.dll.*|
|`AllowedRelatedFileExtensions`|İsteğe `String[]` bağlı parametre.<br /><br /> İlişkili dosyalar için bir arama için kullanmak üzere dosya adı uzantıları. Varsayılan uzantılar *.pdb ve* *.xml.*|
|`AppConfigFile`|İsteğe `String` bağlı parametre.<br /><br /> BindingRedirect *app.config* ayrıştıran ve ayıklanan bir dosya belirtir. Bu parametre belirtilirse parametresi `AutoUnify` `false` olmalıdır.|
|`Assemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Tam yolların ve bağımlılıkların belirlenecek öğeleri belirtir. Bu öğeler "System" gibi basit adlara veya "System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" gibi güçlü adlara sahip olabilir.<br /><br /> Bu parametreye geçirilen öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerine sahip olabilir:<br /><br /> -   `Private`: `Boolean` değeri. ise, `true` öğe yerel olarak kopyalanır. `true` varsayılan değerdir.<br />-   `HintPath`: `String` değeri. Başvuru olarak kullanmak üzere yolu ve dosya adını belirtir. Bu meta veriler, parametresinde {HintPathFromItem} belirtilirken `SearchPaths` kullanılır. Varsayılan değer boş bir dizedir.<br />-   `SpecificVersion`: `Boolean` değeri. ise, `true` öznitelikte belirtilen tam ad `Include` eşleşmesi gerekir. ise, `false` aynı basit adı olan herhangi bir derleme çalışır. `SpecificVersion`Belirtilmezse, görev öğenin özniteliğinde `Include` değeri inceler. Öznitelik basit bir adsa, gibi `SpecificVersion` `false` davranır. Öznitelik, güçlü bir adsa, gibi `SpecificVersion` `true` davranır.<br />     Başvuru öğesi türüyle birlikte kullanılırken, `Include` özniteliğin çözümlenecek derlemenin tam fusion adı olması gerekir. Derleme yalnızca fusion özniteliğiyle tam olarak eşlenirse `Include` çözümlenir.<br />     Bir proje bir .NET Framework sürümünü hedeflese ve daha yüksek bir .NET Framework sürümü için derlenmiş bir derlemeye başvursa, başvuru yalnızca olarak `SpecificVersion` ayarlanmışsa `true` çözümler.<br />     Proje bir profili hedeflese ve profilde yer alan bir derlemeye başvursa, başvuru yalnızca olarak ayarlanmışsa `SpecificVersion` `true` çözümler.<br />-   `ExecutableExtension`: `String` değeri. Mevcut olduğunda, çözümlenen derlemenin bu uzantıya sahip olması gerekir. Eksik olduğunda, *.dll* önce kabul edilir ve ardından *ince.exe* dizin için , kullanılır.<br />-   `SubType`: `String` değeri. Yalnızca boş SubType meta verilerine sahip öğeler tam derleme yollarına çözümlenir. Boş olmayan SubType meta verilerine sahip öğeler yoksayılır.<br />-   `AssemblyFolderKey`: `String` değeri. Bu meta veriler eski amaçlar için de desteklemektedir. Derleme başvurularını çözümlemek için kullanması gereken **hklm \\ \<VendorFolder>** gibi bir kullanıcı tanımlı `Assemblies` kayıt defteri anahtarı belirtir.|
|`AssemblyFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bağımlılıkları bulmak için tam derlemelerin listesini belirtir.<br /><br /> Bu parametreye geçirilen öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerine sahip olabilir:<br /><br /> -   `Private`: isteğe bağlı `Boolean` bir değer. True ise, öğe yerel olarak kopyalanır.<br />-   `FusionName`: isteğe bağlı `String` meta veriler. Bu öğenin basit veya güçlü adını belirtir. Bu öznitelik varsa, derleme dosyasının adı almak için açılması gerekmay olduğundan zaman kaydedebilir.|
|`AutoUnify`|İsteğe `Boolean` bağlı parametre.<br /><br /> Bu parametre, normal birApp.Configdosyasına sahip olamayacak OLAN DLL'ler *gibi derlemeleri derlemek için* kullanılır.<br /><br /> olduğunda, `true` sonuçta elde edilen bağımlılık grafiği otomatik olarak AppConfigFile *parametresineApp.Config* bir dosya var gibi kabul edilir. Bu sanal *App.Config,* çakışan her derleme kümesi için en yüksek sürüm derlemesi seçilecek şekilde bir bindingRedirect girdisine sahip. Bunun bir sonucu, her çakışma çözümlenmiş olduğundan çakışan derlemeler hakkında hiçbir zaman uyarı olmayacaktır.<br /><br /> olduğunda, her ayrı yeniden kırpma eski ve yeni sürümleri ve olan `true` yüksek öncelikli bir açıklamayla `AutoUnify` sonuçlandır. `true`<br /><br /> olduğunda, `true` AppConfigFile parametresi boş olmalıdır.<br /><br /> olduğunda, `false` hiçbir derleme sürümü yeniden zamanlama otomatik olarak oluşmaz. Bir derlemenin iki sürümü mevcut olduğunda bir uyarı çıkar.<br /><br /> olduğunda, `false` aynı derlemenin farklı sürümleri arasındaki her ayrı çakışma yüksek öncelikli bir açıklamayla sonuç verir. Bu açıklamalara tek bir uyarı takip ediliyor. Uyarı benzersiz bir hata koduna sahip ve "Başvuru ve bağımlı derlemelerin farklı sürümleri arasında çakışmalar bulundu" ifadesinin bulunduğu metni içerir.<br /><br /> `false` varsayılan değerdir.|
|`CandidateAssemblyFiles`|İsteğe `String[]` bağlı parametre.<br /><br /> Arama ve çözümleme işlemi için kullanmak üzere derlemelerin listesini belirtir. Bu parametreye geçirilen değerler mutlak dosya adları veya proje göreli dosya adları olmalıdır.<br /><br /> Bu listede derlemeler, parametre dikkate alınacak `SearchPaths` yollardan biri olarak {CandidateAssemblyFiles} içerdiğinde dikkate alınır.|
|`CopyLocalDependenciesWhenParentReferenceInGac`|İsteğe <xref:System.Boolean> bağlı parametre.<br /><br /> True ise, bir bağımlılığın yerel olarak kopyalanmış olup olmadığını belirlemek için yapılan denetimlerden biri, proje dosyasındaki üst başvuruda Özel meta veri kümesi olup olmadığını görmektir. Ayarlanırsa, Özel değeri bağımlılık olarak kullanılır.<br /><br /> Meta veriler ayarlanmazsa bağımlılık, üst başvuruyla aynı denetimler üzerinden gider. Bu denetimlerden biri, başvurusun GAC'de olup olduğunu görmek içindir. Başvuru GAC'de ise, hedef makinedeki GAC'de olduğu varsayılır çünkü yerel olarak kopyalanmaz. Bu yalnızca belirli bir başvuru için geçerlidir, bağımlılıkları için geçerli değildir.<br /><br /> Örneğin, GAC'de yer alan proje dosyasındaki bir başvuru yerel olarak kopyalanmaz, ancak bağımlılıkları GAC'de yer alamayarak yerel olarak kopyalanır.<br /><br /> False ise, proje dosyası başvuruları GAC'de olup olduklarını görmek için denetlenir ve uygun şekilde yerel olarak kopyalanır.<br /><br /> Bağımlılıklar GAC'de olup olduklarını görmek için denetlenir ve ayrıca proje dosyasından üst başvuru gaC'de olup değillerine de denetlenir.<br /><br /> Proje dosyasından üst başvuru GAC'de ise bağımlılık yerel olarak kopyalanmaz.<br /><br /> Bu parametrenin true veya false olması, birden çok üst başvuru olması ve bunların herhangi biri GAC'de yoksa, bunların hepsi yerel olarak kopyalanır.|
|`CopyLocalFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> , , `ResolvedFiles` , ve `ResolvedDependencyFiles` `RelatedFiles` parametrelerinde değerine sahip öğe meta verileri `SatelliteFiles` olan her dosyayı `ScatterFiles` `CopyLocal` `true` döndürür.|
|`FilesWritten`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Diske yazılan öğeleri içerir.|
|`FindDependencies`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise `true` bağımlılıklar bulunur. Aksi takdirde, yalnızca birincil başvurular bulunur. `true` varsayılan değerdir.|
|`FindRelatedFiles`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` *.pdb dosyaları ve* *xml* dosyaları gibi ilgili dosyalar bulunur. `true` varsayılan değerdir.|
|`FindSatellites`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` uydu derlemeleri bulunur. Varsayılan değer: `true.`|
|`FindSerializationAssemblies`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` görev serileştirme derlemelerini arar. `true` varsayılan değerdir.|
|`FullFrameworkAssemblyTables`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bir redist listesini belirli bir çerçeve diziniyle ilişkilendirmek için "FrameworkDirectory" meta verilerine sahip öğeleri belirtir. İlişkililik yoksa bir hata günlüğe kaydedilir. FrameworkDirectory ayarlanmazsa çözüm derleme başvurusu (RAR) mantığı hedef çerçeve dizinini kullanır.|
|`FullFrameworkFolders`|İsteğe <xref:System.String?displayProperty=fullName> `[]` bağlı parametre.<br /><br /> RedistList dizini içeren klasörleri belirtir. Bu dizin, belirli bir istemci profili için tam çerçeveyi temsil eder; örneğin, *%programfiles%\reference assemblies\microsoft\framework\v4.0*.|
|`FullTargetFrameworkSubsetNames`|İsteğe `String[]` bağlı parametre.<br /><br /> Hedef çerçeve alt kümesi adlarının listesini içerir. Listede yer alan bir alt küme adı name özelliğinde bir adla eşlese, sistem derleme zamanında bu hedef çerçeve alt `TargetFrameworkSubset` kümesini dışlar.|
|`IgnoreDefaultInstalledAssemblyTables`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, görev altında \RedistList dizininde bulunan ek yüklü derleme tablolarını `true` *("Redist* Listeleri") arar ve `TargetFrameworkDirectories` kullanır. Varsayılan değer: `false.`|
|`IgnoreDefaultInstalledAssemblySubsetTables`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` görev altında *\SubsetList* dizininde bulunan ek yüklü derleme alt kümesi tablolarını ("Alt Küme Listeleri") arar ve `TargetFrameworkDirectories` kullanır. Varsayılan değer: `false.`|
|`InstalledAssemblySubsetTables`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Hedef alt kümede olması beklenen derlemeleri belirten XML dosyalarının listesini içerir.<br /><br /> Seçenek olarak, bu listede yer alan öğeler bir `InstalledAssemblySubsetTable`<br /><br /> belirli bir çerçeve dizinine sahip.<br /><br /> Yalnızca bir öğe varsa, bu listede "FrameworkDirectory" meta verisi olmayan öğeler, öğesine geçirilen benzersiz değere ayarlanmış `TargetFrameworkDirectories` gibi kabul `TargetFrameworkDirectories` edilir.|
|`InstalledAssemblyTables`|İsteğe `String` bağlı parametre.<br /><br /> Hedef bilgisayarda yüklü olması beklenen derlemeleri belirten XML dosyalarının listesini içerir.<br /><br /> Ayar `InstalledAssemblyTables` olduğunda, listede derlemelerin önceki sürümleri XML'de listelenen daha yeni sürümlerle birleştirilir. Ayrıca, InGAC='true' ayarına sahip derlemeler önkoşul olarak kabul edilir ve açıkça geçersiz kılınmadıkça CopyLocal='false' olarak ayarlanır.<br /><br /> Seçenek olarak, bu listede öğeler belirli bir çerçeve diziniyle ilişkilendirmek için "FrameworkDirectory" `InstalledAssemblyTable` meta verilerini belirtebilirsiniz.  Ancak, Redist adı ile başlayana kadar bu ayar yoksayılır<br /><br /> "Microsoft-Windows-CLRCoreComp".<br /><br /> Yalnızca bir öğe varsa, bu listede "FrameworkDirectory" meta verisi olmayan öğeler geçirilen benzersiz değere ayarlanmış gibi `TargetFrameworkDirectories` kabul edilir<br /><br /> için `TargetFrameworkDirectories` .|
|`LatestTargetFrameworkDirectories`|İsteğe `String[]` bağlı parametre.<br /><br /> Makinede hedeflen en güncel çerçeve için redist listelerini içeren dizinlerin listesini belirtir. Bu ayarlanmazsa, makinede yüklü olan en yüksek çerçeve, verilen bir hedef çerçeve tanımlayıcısı için kullanılır.|
|`ProfileName`|İsteğe `String` bağlı parametre.<br /><br /> - Hedeflen çerçeve profilinin adını belirtir. Örneğin, İstemci, Web veya Ağ.|
|`RelatedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Başvuruyla aynı temel adı olan XML ve *.pdb* dosyaları gibi ilgili dosyaları içerir.<br /><br /> Bu parametrede listelenen dosyalar isteğe bağlı olarak aşağıdaki öğe meta verilerini içerebilir:<br /><br /> -   `Primary`: `Boolean` değeri. ise, `true` dosya öğesi parametresi kullanılarak diziye `Assemblies` geçirildi. Varsayılan değer `false` olarak belirlenmiştir.<br />-   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.|
|`ResolvedDependencyFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Bağımlılıkların *n.* sıra yollarını içerir. Bu parametre, parametresinde yer alan ilk sipariş birincil başvurularını `ResolvedFiles` içermez.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.<br />-   `FusionName`: `String` değeri. Bu bağımlılığın adını belirtir.<br />-   `ResolvedFrom`: `String` değeri. Bu dosyanın çözümlenmiş olduğu değişmez arama yolunu belirtir.|
|`ResolvedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Tam yollara çözümlenen tüm birincil başvuruların listesini içerir.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.<br />-   `FusionName`: `String` değeri. Bu bağımlılığın adını belirtir.<br />-   `ResolvedFrom`: `String` değeri. Bu dosyanın çözümlenmiş olduğu değişmez arama yolunu belirtir.|
|`SatelliteFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Bulunan tüm uydu dosyalarını belirtir. Bu öğenin varolmalarına neden olan başvuru veya bağımlılık CopyLocal=true ise bunlar CopyLocal=true olur.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir. Bu değer, `true` bu öğenin var olması için neden olan başvuru veya bağımlılığın değerine sahip `CopyLocal` `true` olmasıdır.<br />-   `DestinationSubDirectory`: `String` değeri. Bu öğeyi kopyalamak için göreli hedef dizini belirtir.|
|`ScatterFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Verilen derlemelerden biri ile ilişkili dağılım dosyalarını içerir.<br /><br /> Bu parametredeki öğeler isteğe bağlı olarak aşağıdaki öğe meta verilerini içerir:<br /><br /> -   `CopyLocal`: `Boolean` değeri. Verilen başvuru çıktı dizinine kopyalanır olup olmadığını gösterir.|
|`SearchPaths`|Gerekli `String[]` parametre.<br /><br /> Derlemeleri temsil eden diskte dosyaları bulmak için aranan dizinleri veya özel konumları belirtir. Arama yollarının liste sırası önemlidir. Her derleme için yol listesi soldan sağa aranır. Derlemeyi temsil eden bir dosya bulunursa, bu arama durur ve sonraki derleme için arama başlar.<br /><br /> Bu parametre, aşağıdaki listeden dizin yolları veya özel değişmez değerler olan noktalı virgülle ayrılmış değerler listesini kabul eder:<br /><br /> -   `{HintPathFromItem}`: Görevin temel öğenin meta `HintPath` verilerini inceleyeceklerini belirtir.<br />-   `{CandidateAssemblyFiles}`: Görevin parametresi aracılığıyla geçirilen dosyaları inceleyeceklerini `CandidateAssemblyFiles` belirtir.<br />-   `{Registry:`\<AssemblyFoldersBase>, \<RuntimeVersion> , : Görevin kayıt defterinde belirtilen ek \<AssemblyFoldersSuffix> `}` klasörlerde aranacak olduğunu belirtir. \<AssemblyFoldersBase>, \<RuntimeVersion> , \<AssemblyFoldersSuffix> ve, aranacak kayıt defteri konumu için belirli değerlerle değiştir değiştiri. Ortak hedeflerde varsayılan belirtim şu şekildedir: {Registry:$(FrameworkRegistryBase), $(TargetFrameworkVersion), $(AssemblyFoldersSuffix), $(AssemblyFoldersExConditions)}.<br />-   `{AssemblyFolders}`: Görevin Visual Studio.NET 2003 finding-assemblies-from-registry şemasını kullanmayacaklarını belirtir.<br />-   `{GAC}`: Görevin Genel Derleme Önbelleği'nde (GAC) aranacak olduğunu belirtir.<br />-   `{RawFileName}`: Görevin öğenin değerini tam `Include` bir yol ve dosya adı olarak değerlendireceklerini belirtir.|
|`SerializationAssemblyFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Bulunan tüm XML serileştirme derlemelerini içerir. Bu öğeler copyLocal=true ise ve yalnızca bu öğenin varolmalarına neden olan başvuru veya bağımlılık CopyLocal=true ise işaretlenir.<br /><br /> `Boolean`CopyLocal meta verileri verilen başvuruya çıkış dizinine kopyalayıp kopyalanmay gerektiğini gösterir.|
|`Silent`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` hiçbir ileti günlüğe kaydedilmez. `false` varsayılan değerdir.|
|`StateFile`|İsteğe `String` bağlı parametre.<br /><br /> Bu görev için ara derleme durumunun nereye kaydediLn olduğunu belirten bir dosya adı belirtir.|
|`SuggestedRedirects`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur çıkış parametresi.<br /><br /> Parametrenin değerinden bağımsız olarak, her ayrı çakışan derleme kimliği için bir öğe `AutoUnify` içerir. Bu, uygulama yapılandırma dosyasında uygun bindingRedirect girdisi olmayan bulunan her kültürü ve PKT'yi içerir.<br /><br /> İsteğe bağlı olarak her öğe aşağıdaki bilgileri içerir:<br /><br /> -   `Include` attribute: Sürüm alanı değeri 0.0.0.0 olan derleme ailesinin tam adını içerir<br />-   `MaxVersion` öğe meta verileri: En fazla sürüm numarasını içerir.|
|`TargetedRuntimeVersion`|İsteğe `String` bağlı parametre.<br /><br /> Hedef çalışma zamanı sürümünü belirtir, örneğin, 2.0.57027 veya v2.0.57027.|
|`TargetFrameworkDirectories`|İsteğe `String[]` bağlı parametre.<br /><br /> Hedef çerçeve dizininin yolunu belirtir. Bu parametre, sonuçta elde edilen öğeler için CopyLocal durumunu belirlemek için gereklidir.<br /><br /> Bu parametre belirtilmezse, kaynak öğelerinde açıkça meta veri değeri olmadığı sürece sonuçta elde edilen öğelerin CopyLocal `true` `Private` değeri `true` olmaz.|
|`TargetFrameworkMoniker`|İsteğe `String` bağlı parametre.<br /><br /> Varsa, izlenir TargetFrameworkMoniker. Bu günlük kaydı için kullanılır.|
|`TargetFrameworkMonikerDisplayName`|İsteğe `String` bağlı parametre.<br /><br /> Varsa, izlenir TargetFrameworkMoniker'ın görünen adı. Bu günlük kaydı için kullanılır.|
|`TargetFrameworkSubsets`|İsteğe `String[]` bağlı parametre.<br /><br /> Hedef çerçeve dizinleri içinde aranacak hedef çerçeve alt kümesi adlarının listesini içerir.|
|`TargetFrameworkVersion`|İsteğe `String` bağlı parametre.<br /><br /> Proje hedef çerçevesi sürümü. Varsayılan değer boştur, yani hedef çerçeveye göre başvurular için filtreleme yoktur.|
|`TargetProcessorArchitecture`|İsteğe `String` bağlı parametre.<br /><br /> Tercih edilen hedef işlemci mimarisi. Genel Derleme Önbelleği (GAC) başvurularını çözümlemek için kullanılır.<br /><br /> Bu parametre , veya `x86` `IA64` değerine sahip `AMD64` olabilir.<br /><br /> Bu parametre yoksa, görev önce o anda çalışan sürecin mimarisiyle eşan derlemeleri dikkate almaktadır. Hiçbir derleme bulunamasa, görev GAC'de değerine sahip veya hiç değere sahip `ProcessorArchitecture` `MSIL` derlemeleri göz önünde `ProcessorArchitecture` bulundurrarak.|

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

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
