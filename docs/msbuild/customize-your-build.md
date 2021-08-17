---
title: Derlemenizi özelleştirme | Microsoft Docs
description: Standart derleme işlemini kullanan projeleri özelleştirmek için kullanabileceğiniz MSBuild genişletilebilirlik kancaları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: bf19be21d95c4ac271772e8101e0c077e5af7f55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123365"
---
# <a name="customize-your-build"></a>Derlemenizi özelleştirme

MSBuild işlemini kullanan tüm projelerde *(Microsoft.Common.props* ve *Microsoft.Common.targets* içeri aktarıyor) derleme işleminizi özelleştirmek için kullanabileceğiniz çeşitli genişletilebilirlik kancaları vardır.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Projeniz için komut satırı MSBuild bağımsız değişkenleri ekleme

Kaynak *dizininizin veya üzerindeki Bir Directory.Build.rsp* dosyası projenizin komut satırı derlemeleri için uygulanır. Ayrıntılar için [bkz. MSBuild dosyaları.](../msbuild/msbuild-response-files.md#directorybuildrsp)

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props ve Directory.Build.targets

Sürüm 15 MSBuild i oluşturmadan önce, çözümdeki projelere yeni, özel bir özellik sağlamak istediyebilirsiniz. Bu özellik için çözümdeki her proje dosyasına el ile başvuru eklemeniz gerekirdi. Veya özelliğini bir *.props* dosyasında tanımlamanız ve ardından çözümde yer alan her projede *.props* dosyasını açıkça içeri aktarmanız gerekirdi.

Ancak, artık bir adımda her projeye, kaynağınızı içeren kök klasörde *Directory.Build.props* adlı tek bir dosyada tanımlayarak yeni bir özellik ekebilirsiniz. Bu MSBuild *Microsoft.Common.props,* *Directory.Build.props* dosyası için dizin yapınızı arar *(ve Microsoft.Common.targets,* *Directory.Build.targets dosyasını arar).* Bir tane bulursa, özelliğini içeri aktarıyor. *Directory.Build.props,* bir dizin altındaki projelere özelleştirmeler sağlayan kullanıcı tanımlı bir dosyadır.

> [!NOTE]
> Linux tabanlı dosya sistemleri büyük/büyük/büyük harfe duyarlıdır. Directory.Build.props dosya adı büyük/yeni dosya adı ile tam olarak eşlandığından emin olun, yoksa derleme işlemi sırasında algılanmaz.
>
> Daha [fazla GitHub için bu](https://github.com/dotnet/core/issues/1991#issue-368441031) soruna bakın.

### <a name="directorybuildprops-example"></a>Directory.Build.props örneği

Örneğin, tüm projelerinizi yeni Roslyn **/deterministic** özelliğine (özelliği tarafından Roslyn hedefine açık olan) erişmesi için etkinleştirmek için `CoreCompile` `$(Deterministic)` aşağıdakini yapabilirsiniz.

1. Repo'nizin kökünde *Directory.Build.props* adlı yeni bir dosya oluşturun.
2. Dosyaya aşağıdaki XML'yi ekleyin.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. MSBuild. Projenizin *Mevcut Microsoft.Common.props* ve *Microsoft.Common.targets* içeri aktarmaları dosyayı bulur ve içeri aktarır.

### <a name="search-scope"></a>Arama kapsamı

*Bir Directory.Build.props* dosyasını ararken, MSBuild dizin yapısını proje konumunuzdan () yukarı doğru ilerler ve `$(MSBuildProjectFullPath)` Bir *Directory.Build.props* dosyasını bu bulunduktan sonra durduruluyor. Örneğin, `$(MSBuildProjectFullPath)` *c:\users\username\code\test\case1* ise MSBuild, aşağıdaki dizin yapısında olduğu gibi *bir Directory.Build.props* dosyasını bulana kadar dizin yapısını yukarı doğru aramaya başlar.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Çözüm dosyasının konumu *Directory.Build.props ile ilgisiz.*

### <a name="import-order"></a>İçeri aktarma siparişi

*Directory.Build.props,* *Microsoft.Common.props* içinde çok erken bir şekilde içe aktarılır ve daha sonra tanımlanan özellikler tarafından kullanılamaz. Bu nedenle, henüz tanımlanmamış (ve boş olarak değerlendirilecek) özelliklere başvuru yapmaktan kaçının.

*Directory.Build.props* içinde ayarlanmış özellikler proje dosyasının veya içe aktarılan dosyaların başka bir yerinde geçersiz kılınabilir. Bu *nedenle, Directory.Build.props'daki* ayarları projeleriniz için varsayılan değerleri belirterek düşünebilirsiniz.

*Directory.Build.targets,* paketlerden *.targets* dosyaları içeri aktarıldıktan sonra *Microsoft.Common.targets'NuGet* alınır. Bu nedenle, derleme mantığının çoğunda tanımlanan özellikleri ve hedefleri geçersiz kabilirsiniz veya tek tek projelerin ne ayarlansa da tüm projeleriniz için özellikleri ayarlayın.

Bir özellik ayarlamanız veya önceki ayarları geçersiz kacak tek bir proje için hedef tanımlamanız gerekirken, bu mantığı son içeri aktarmadan sonra proje dosyasına ekleyin. Bunu SDK stili bir projede yapmak için önce SDK stili özniteliğini eşdeğer içeri aktarmalarla değiştirmeniz gerekir. Bkz. [MSBuild proje SDK'lerini kullanma.](how-to-use-project-sdk.md)

> [!NOTE]
> MSBuild altyapısı, herhangi bir proje için derleme yürütmeyi başlatmadan önce değerlendirme sırasında içe aktarılan tüm dosyalarda okur (herhangi biri dahil), dolayısıyla bu dosyaların derleme işleminin veya başka bir bölümü tarafından `PreBuildEvent` `PreBuildEvent` değiştirilmeleri beklenmiyor. Herhangi bir değişiklik, bir sonraki derleme  veya sonrakiMSBuild.exeçağrılıncaya kadar Visual Studio olmaz.

### <a name="use-case-multi-level-merging"></a>Kullanım durumu: çok düzeyli birleştirme

Bu standart çözüm yapısına sahip olduğunu varsayalım:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Tüm projeler *(1)* için ortak özelliklere, *src* projeleri *için ortak özelliklere (2-src)* ve *test* projeleri için ortak *özelliklere (2-test)* sahip olmak iyi olabilir.

"iç" MSBuild (*2-src* ve *2-test*) "dış" dosyası (*1)* ile doğru şekilde birleştirmek için, MSBuild *bir Directory.Build.props* dosyası bulduğunda daha fazla taramanın durdur olduğunu göz önünde bulundurabilirsiniz. Taramaya ve dış dosyada birleştirmeye devam etmek için bu kodu iki iç dosyaya da girin:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild yaklaşımının özeti şöyledir:

- Belirli bir proje için MSBuild çözüm yapısında *ilk Directory.Build.props'ı* bulur, varsayılan değerlerle bir değiştirir ve daha fazlasını taramayı durdurur
- Birden çok düzeyin bulunarak birleştirilmiş olması için [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) "iç" dosyadan "dış" dosya (yukarıda gösterilmiştir)
- "Dış" dosyanın kendisi de üzerine bir şey aktaramazsa tarama orada durur
- Tarama/birleştirme işlemini kontrol etmek için ve `$(DirectoryBuildPropsPath)` kullanın `$(ImportDirectoryBuildProps)`

Daha basitçe ifade etmek gerekirse, hiçbir şeyi içeri aktarmadan ilk *Directory.Build.props,* MSBuild durur.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>.props veya .targets dosyasına özellik ekleme arasında seçim

MSBuild sırasına bağlıdır ve bir özelliğin (veya veya `UsingTask` hedefin) son tanımı kullanılan tanımdır.

Açık içeri aktarmaları kullanırken herhangi bir noktada *bir .props* veya *.targets* dosyasından içeri aktarabilirsiniz. Yaygın olarak kullanılan kural şu şekildedir:

- *.props* dosyaları içeri aktarma sırasına göre erken içeri aktarılır.

- *.targets*  dosyaları derleme sırasına geç aktarıldı.

Bu kural içeri aktarmalar tarafından zorunlu kılınır (diğer bir ifadeyle Sdk.props içeri aktarması önce, dosyanın tüm içeriği `<Project Sdk="SdkName">` öncesinde, *sdk.targets* ise dosyanın tüm içeriklerinin ardından son olarak  gelir).

Özellikleri nereye koyarak karar verirken aşağıdaki genel yönergeleri kullanın:

- Birçok özellik için nerede tanımlandığı önemli değildir çünkü bunlar üzerine yazılmaz ve yürütme zamanında salt okunur olur.

- Tek bir projede özelleştirebileceğiniz davranışlar için *.props* dosyalarında varsayılanları ayarlayın.

- Özelleştirme, kullanıcının projesini okuyana kadar MSBuild özelliğinin değerini okuyarak *.props* dosyalarında bağımlı özellikler ayarlamayın.

- Tek tek *projelerden özelleştirmeleri* alacakları için .targets dosyalarında bağımlı özellikler ayarlayın.

- Özellikleri geçersiz kılmanız gerekirse, tüm kullanıcı projesi özelleştirmeleri etkili olma şansına sahip olduktan sonra bunu bir *.targets* dosyasında yap. Türetilmiş özellikleri kullanırken dikkatli olun; türetilmiş özelliklerin de geçersiz kılınmış olması gerekir.

- *Öğeleri .props dosyalarına* dahil etmek (bir özellikte koşullandı). Tüm özellikler herhangi bir öğeden önce dikkate alınır, bu nedenle kullanıcı projesi özellik özelleştirmeleri alınır ve bu, kullanıcının projesine veya içeri aktarma tarafından getirilen herhangi bir `Remove` `Update` öğeye fırsat verir.

- *.targets dosyalarında hedefleri* tanımlayın. Ancak, *.targets* dosyası bir SDK tarafından içe aktarıldı ise, kullanıcının projesi varsayılan olarak bunu geçersiz kılmış bir yere sahip olmadığını çünkü bu senaryonun hedefi geçersiz kılmayı zorlaştırmış olduğunu unutmayın.

- Mümkünse, bir hedef içindeki özellikleri değiştirmek yerine değerlendirme zamanında özellikleri özelleştirmeyi tercih edersiniz. Bu kılavuz, projeyi yükleme ve ne yaptığını anlamayı kolaylaştırır.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Varsayılan *olarak, Microsoft.Common.props* içeri `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` aktarmaları ve *Microsoft.Common.targets içeri* aktarıyor. `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets` Varsayılan değeri `MSBuildProjectExtensionsPath` `$(BaseIntermediateOutputPath)` , 'dır. `obj/` NuGet paketlerle birlikte gelen derleme mantığına başvurmak için bu mekanizmayı kullanır; diğer bir ifadeyle, geri yükleme `{project}.nuget.g.props` zamanında paket içeriğine başvuran dosyalar oluşturur.

Özelliğini Directory.Build.props içinde olarak ayarerek veya Microsoft.Common.props'ı içeri aktarmadan önce bu genişletilebilirlik `ImportProjectExtensionProps` `false` mekanizmasını *devre dışı genişletilebilirlik mekanizmasını devre dışı abilirsiniz.* 

> [!NOTE]
> MSBuildProjectExtensionsPath içeri aktarmalarının devre dışı bırakılması, NuGet paketlerde teslim edilen derleme mantığının projenize uygulanmasına engel olur. Bazı NuGet paketleri, işlevlerini gerçekleştirmek için derleme mantığı gerektirir ve bu devre dışı bırakılmıştır.

## <a name="user-file"></a>.user dosyası

*Varsa Microsoft.Common.CurrentVersion.targets* içeri aktarmalarını kullanır, bu nedenle bu ek uzantıyla `$(MSBuildProjectFullPath).user` projenizin yanında bir dosya oluşturabilirsiniz. Kaynak denetimine iade etmek istediğiniz uzun süreli değişiklikler için projenin kendisini değiştirmeyi tercih edin; böylece gelecekteki bakımcılar bu uzantı mekanizmasını bilmek zorunda değildir.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath ve MSBuildUserExtensionsPath

> [!WARNING]
> Bu uzantı mekanizmalarını kullanmak, makineler arasında yinelenebilir derlemeler elde etmek daha zor hale geldi. Kaynak denetim sisteminize iade edilen ve kod tabanınızı tüm geliştiriciler arasında paylaştıran bir yapılandırma kullanmayı deneyin.

Kural gereği, birçok temel derleme mantığı dosyası içeri aktar

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

içeriklerinden önce ve

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

Sonra. Bu kural, ortak proje türlerinin derleme mantığını artırmak için yüklü OLAN SDK'lere olanak sağlar.

`$(MSBuildUserExtensionsPath)` *%LOCALAPPDATA%\Microsoft\MSBuild*. Bu klasöre yerleştirilen dosyalar, ilgili proje türünün ilgili kullanıcının kimlik bilgileri altında çalıştırılmış olan tüm derlemeleri için içe aktarılır. desende içeri aktarma dosyasından sonra adlı özellikleri ayarerek kullanıcı uzantılarını devre dışı `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` abilirsiniz. Örneğin, olarak `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` `false` ayarı, içeri aktarmayı `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` önler.

## <a name="customize-the-solution-build"></a>Çözüm derlemeyi özelleştirme

> [!IMPORTANT]
> Çözüm derlemesini bu şekilde özelleştirmek yalnızcaMSBuild.exeile komut *satırı derlemeleri için geçerlidir.* Uygulamanın **içindeki** derlemeler için Visual Studio. Bu nedenle, özelleştirmenin çözüm düzeyinde kullanılması önerilmez. Bir çözümdeki tüm projeleri özelleştirmenin daha iyi bir alternatifi, bu makalenin başka bir yerinde ele alınarak çözüm *klasöründeki Directory.Build.props* ve *Directory.build.targets* dosyalarını kullanmaktır.

Bu MSBuild bir çözüm dosyası derlemesi, önce bir proje dosyasına dahili olarak çevirir ve sonra bunu derlemeye devam ediyor. Oluşturulan proje dosyası, herhangi bir hedefi tanımlamadan önce ve ve dizinlerine yüklenmiş hedefler de dahil olmak üzere hedefleri içeri `before.{solutionname}.sln.targets` `after.{solutionname}.sln.targets` aktarmadan `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` önce içeri aktarma `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` işlemidir.

Örneğin, *myCustomizedSolution.sln* dosyasını oluşturduktan sonra aynı dizinde adlı bir dosya oluşturarak özel günlük iletisi yazmak için yeni bir hedef *tanımlayabilirsiniz. Içeren MyCustomizedSolution.sln.targets*

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

Çözüm derlemesi proje derlemelerinden ayrıdır, bu nedenle buradaki ayarlar proje derlemelerini etkilemez.

## <a name="customize-all-net-builds"></a>Tüm .NET derlemelerini özelleştirme

Derleme sunucusunu korurken, sunucu üzerinde tüm derlemeler MSBuild genel olarak yapılandırmaniz gerekebilir.  Prensipte, genel *Microsoft.Common.Targets* veya *Microsoft.Common.Props* dosyalarını değiştirebilirsiniz, ancak daha iyi bir yol vardır. Belirli bir proje türünün (tüm C# projeleri gibi) tüm derlemelerini, belirli MSBuild ve dosyaları ekleyerek `.targets` `.props` etkileyebilirsiniz.

MSBuild veya Visual Studio yüklemesi tarafından yönetilen tüm C# veya Visual Basic derlemelerini etkilemesi için, *Microsoft.Common.targets* öncesinde veya sonrasında çalıştıracak hedeflerle *Custom.Before.Microsoft.Common.Targets* veya *Custom.After.Microsoft.Common.Props* dosyası ya da Microsoft.Common.props öncesinde veya sonrasında işlenecek özelliklerle  *Custom.Before.Microsoft.Common.Props* dosyası oluşturun. 

Bu dosyaların konumlarını belirtmek için aşağıdaki MSBuild kullanabilirsiniz:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Bu *özelliklerin* Ortak sürümleri hem C# hem de Visual Basic etkiler. Bu özellikleri komut satırına MSBuild kurabilirsiniz.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

En iyi yaklaşım senaryoya bağlıdır. Genişletilebilirlik Visual Studio kullanarak derleme sistemini özelleştirilebilir ve özelleştirmeleri yüklemek ve yönetmek için bir mekanizma sebilirsiniz.

Ayrılmış bir derleme sunucunuz varsa ve belirli hedeflerin her zaman bu sunucuda yürütülen uygun proje türüne sahip tüm derlemelerde yürütülür olmasını sağlamak için genel bir özel veya dosya `.targets` `.props` kullanmak mantıklıdır.  Özel hedeflerin yalnızca belirli koşullar geçerli olduğunda yürütmesi için, başka bir dosya konumu kullanın ve MSBuild komut satırına uygun MSBuild özelliğini yalnızca gerektiğinde ayarerek bu dosyanın yolunu ayarlayın.

> [!WARNING]
> Visual Studio, eşleşen türde herhangi bir proje derlemesinde MSBuild klasöründe bulursa özel `.targets` `.props` veya dosyaları kullanır. Bu, yanlışlıkla sonuçlar doğurabilir ve yanlış yapılırsa, bilgisayarınızda derleme Visual Studio devre dışı bırakabilir.

## <a name="customize-c-builds"></a>C++ derlemelerini özelleştirme

C++ projeleri için, daha önce bahsedilen *özel .targets* ve *.props* dosyaları varsayılan ayarları geçersiz kılmak için aynı şekilde kullanılamaz. *Directory.Build.props,* *Microsoft.Common.props* tarafından içe aktarılır. Varsayılanların çoğu `Microsoft.Cpp.Default.props` *Microsoft.Cpp.props* içinde tanımlanırken ve bir dizi özellik için "henüz tanımlanmamışsa" koşulu kullanılamaz, çünkü özellik zaten tanımlanmıştır, ancak ile tanımlanan belirli proje özellikleri için varsayılan değerin farklı olması gerekir `PropertyGroup` (bkz. `Label="Configuration"` [.vcxproj ve .props dosya yapısı).](/cpp/build/reference/vcxproj-file-structure)

Ancak, *Microsoft.Cpp dosyalarından \** önce/sonra otomatik olarak içe aktar edilecek *.props* dosyalarını belirtmek için aşağıdaki özellikleri kullanabilirsiniz:

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Tüm C++ derlemeleri için özelliklerin varsayılan değerlerini özelleştirmek için, başka bir *.props* dosyası *(örneğin, MyProps.props)* oluşturun ve özelliği işaret ediyor `ForceImportAfterCppProps` olarak `Directory.Build.props` tanımlayın:

<PropertyGroup><ForceImportAfterCppProps>$(MsbuildThisFileDirectory)\MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

*MyProps.props,* *Microsoft.Cpp.props'ın en sonunda otomatik olarak içe aktarılır.*

## <a name="customize-all-c-builds"></a>Tüm C++ derlemelerini özelleştirme

Visual Studio yüklemesini özelleştirmeniz önerilmez çünkü bu tür özelleştirmeleri izlemek kolay değildir, ancak Visual Studio'yi belirli bir platform için C++ derlemelerini özelleştirmek üzere genişletıyorsanız, her platform için dosya oluşturabilir ve bunları bir Visual Studio uzantısının parçası olarak bu platformlar için uygun içeri aktarma klasörlerine yer `.targets` veebilirsiniz.

`.targets`Win32 platformu *Microsoft.Cpp.Win32.targets* dosyası aşağıdaki öğeyi `Import` içerir:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Aynı dosyanın sonuna yakın benzer bir öğe vardır:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

*%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platforms içinde diğer hedef platformlar için benzer içeri aktarma öğeleri \* vardır.

Dosyayı platforma göre uygun klasöre yer MSBuild platform için her `.targets` `ImportAfter` C++ derlemesine içeri aktarabilirsiniz. Gerekirse buraya `.targets` birden çok dosya koyabilirsiniz. 

Genişletilebilirlik Visual Studio yeni bir platform tanımlama gibi başka özelleştirmeler de mümkündür. Daha fazla bilgi için [bkz. C++ proje genişletilebilirliği.](../extensibility/visual-cpp-project-extensibility.md)

### <a name="specify-a-custom-import-on-the-command-line"></a>Komut satırı üzerinde özel içeri aktarma belirtme

C++ projesinin belirli bir derlemesi için dahil etmek istediğiniz özel için, ve komut satırı özelliklerinin `.targets` birini veya ikisini birden `ForceImportBeforeCppTargets` `ForceImportAfterCppTargets` ayarlayın.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Genel bir ayar için (örneğin, derleme sunucusundaki bir platform için tüm C++ derlemelerini etkiler), iki yöntem vardır. İlk olarak, bu özellikleri her zaman ayarlanmış bir sistem ortam değişkeni kullanarak ayarlayabilirsiniz. Bu, MSBuild her zaman ortamı okuduğu ve tüm ortam değişkenleri için (veya geçersiz kılmalar) özellikler oluşturduğu için çalışır.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
