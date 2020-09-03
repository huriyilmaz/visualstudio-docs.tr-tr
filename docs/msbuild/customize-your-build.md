---
title: Derlemenizi özelleştirin | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c52c6b584db94ff3cbe8dc041c00ebe969c9faf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288942"
---
# <a name="customize-your-build"></a>Derlemenizi özelleştirme

Standart derleme işlemini kullanan MSBuild projeleri ( *Microsoft. Common. props* ve *Microsoft. Common. targets*içeri aktarılırken), yapı işleminizi özelleştirmek için kullanabileceğiniz çeşitli genişletilebilirlik kancalarına sahiptir.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Projeniz için komut satırı MSBuild çağırmaları için bağımsız değişkenler ekleyin

Kaynak dizininizin içindeki veya üzerindeki bir *Dizin. Build. rsp* dosyası, projenizin komut satırı yapılarına uygulanır. Ayrıntılar için bkz. [MSBuild yanıt dosyaları](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory. Build. props ve Directory. Build. targets

MSBuild sürüm 15 ' ten önce, çözümünüzde projelere yeni, özel bir özellik sağlamak istiyorsanız, çözümdeki her proje dosyasında bu özelliğe bir başvuruyu el ile eklemeniz gerekiyordu. Ya da, özelliği bir *. props* dosyasında tanımlamanız gerekiyordu ve sonra *. props* dosyasını çözümdeki her projede, diğer şeyler arasında açıkça içeri aktarmalısınız.

Ancak artık, kaynağınızı içeren kök klasörde *Dizin. Build. props* adlı tek bir dosyada tanımlayarak her projeye yeni bir özellik ekleyebilirsiniz. MSBuild çalıştırıldığında, *Microsoft. Common. props* dizin yapınızı *Dizin. Build. props* dosyası (ve *Microsoft. Common. targets* için *Directory. Build. targets*arar) arar. Bir bulursa, özelliği içeri aktarır. *Directory. Build. props* , bir dizin altındaki projelere özelleştirmeler sağlayan Kullanıcı tanımlı bir dosyadır.

> [!NOTE]
> Linux tabanlı dosya sistemleri büyük/küçük harfe duyarlıdır. Directory. Build. props dosya adının büyük/küçük harf olarak eşleştiğinden emin olun veya yapı işlemi sırasında algılanmayacaktır.
>
> Daha fazla bilgi için [Bu GitHub sorununa](https://github.com/dotnet/core/issues/1991#issue-368441031) bakın.

### <a name="directorybuildprops-example"></a>Directory. Build. props örneği

Örneğin, tüm projelerinizi yeni Roslyn **/belirleyici** özelliğine erişecek şekilde etkinleştirmek istiyorsanız (özelliği tarafından Roslyn `CoreCompile` hedefinde gösterilir `$(Deterministic)` ), aşağıdakileri yapabilirsiniz.

1. Deponuzın kök dizininde *Dizin. Build. props*adlı yeni bir dosya oluşturun.
2. Aşağıdaki XML dosyasını dosyaya ekleyin.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. MSBuild 'i çalıştırın. Projenizin mevcut *Microsoft. Common. props* ve *Microsoft. Common. targets* içeri aktarmaları dosyayı bulup içeri aktarır.

### <a name="search-scope"></a>Arama kapsamı

Bir *Dizin. Build. props* dosyası ararken, MSBuild, dizin yapısını proje konumınızdan () yukarı doğru `$(MSBuildProjectFullPath)` bir şekilde gösterir. bir dizin bulduktan sonra durduruluyor. *Build. props* dosyası. Örneğin, Eğer dosyanız `$(MSBuildProjectFullPath)` *username\code\test\case1*ise, MSBuild orada aramaya başlar ve dizin yapısını bir *Dizin. Build. props* dosyası bulunana kadar yukarı doğru bir şekilde arar.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Çözüm dosyasının konumu, *Directory. Build. props*ile ilgisizdir.

### <a name="import-order"></a>İçeri aktarma sırası

*Directory. Build. props* , *Microsoft. Common. props*içinde çok erken içeri aktarılır ve daha sonra tanımlanan özellikler kullanılamaz. Bu nedenle, henüz tanımlanmayan özelliklere başvurmaktan kaçının (ve boş olarak değerlendirilir).

*Directory. Build. props* içinde ayarlanan özellikler proje dosyasında ya da içeri aktarılan dosyalardaki başka bir yerde geçersiz kılınabilir, bu nedenle, projelerinize yönelik Varsayılanları belirterek *Dizin. Build. props* içindeki ayarları düşünmeniz gerekir.

*Dizin. Build. targets* , NuGet paketlerindeki *. targets* dosyalarını içeri aktardıktan sonra *Microsoft. Common. targets* 'dan içeri aktarılır. Bu nedenle, derleme mantığının çoğunda tanımlanan özellikleri ve hedefleri geçersiz kılabilir veya tek tek projelerin ne kadar ayarlandığına bakılmaksızın tüm projeleriniz için özellikleri ayarlayabilirsiniz.

Önceki ayarları geçersiz kılan tek bir proje için bir özellik ayarlamanız veya hedef tanımlamanız gerektiğinde, bu mantığı son içeri aktarma işleminden sonra proje dosyasına koyun. Bunu bir SDK stili projesinde yapmak için, önce SDK stili özniteliğini eşdeğer içeri aktarımlarla değiştirmeniz gerekir. Bkz. [MSBuild proje SDK 'larını kullanma](how-to-use-project-sdk.md).

> [!NOTE]
> MSBuild altyapısı, herhangi bir proje (any dahil) için derleme yürütmeyi başlatmadan önce, tüm içeri aktarılan dosyalarda geliştirme sırasında okur `PreBuildEvent` , bu nedenle bu dosyaların `PreBuildEvent` yapı işleminin veya diğer herhangi bir bölümü tarafından değiştirilmesi beklenmez. Tüm değişiklikler *MSBuild.exe* bir sonraki çağrıya veya sonraki Visual Studio derlemesi tamamlanana kadar etkili olmaz.

### <a name="use-case-multi-level-merging"></a>Kullanım örneği: çok düzeyli birleştirme

Bu standart çözüm yapısına sahip olduğunuzu varsayalım:

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

Tüm projeler *(1)* için ortak özellikler, *src* projeleri için ortak özellikler *(2-src)* ve *Test* projelerine ilişkin ortak özellikler *(2-test)* için ortak özellikler olması istenebilir.

MSBuild 'i "dış" dosya (*1*) ile "iç" dosyaları (*2-src* ve *2-test*) doğru bir şekilde birleştirmek Için, MSBuild bir *Dizin. Build. props* dosyası bulduktan sonra, daha fazla tarama işlemini durdurduğunu dikkate almanız gerekir. Taramaya devam etmek ve dış dosyayla birleştirmek için, bu kodu hem iç dosyalara yerleştirin:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild 'in genel yaklaşımının Özeti aşağıdaki gibidir:

- MSBuild, belirli bir proje için ilk dizini bulur *. Build. props* öğesini çözüm yapısında yukarı doğru birleştirir, varsayılana göre birleştirir ve daha fazlasını taramayı durduruyor
- Birden çok düzeyin bulunmasını ve birleştirilmesini istiyorsanız, [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) "iç" dosyadan "dış" dosya
- "Dış" dosya kendisine ait bir şeyi de içeri aktarmadıysanız, tarama bunu durdur
- Tarama/birleştirme işlemini denetlemek için `$(DirectoryBuildPropsPath)` ve kullanın `$(ImportDirectoryBuildProps)`

Ya da daha fazla: herhangi bir şeyi içeri aktarmaz ilk *Dizin. Build. props* , MSBuild 'in durduğu yerdir.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Bir. props veya. targets dosyasına özellik ekleme arasında seçim yapın

MSBuild içeri aktarma-sipariş bağımlıdır ve bir özelliğin (ya da `UsingTask` hedefin) son tanımı kullanılan tanımdır.

Açık içeri aktarmalar kullanılırken, herhangi bir noktada bir *. props* veya *. targets* dosyasından içeri aktarabilirsiniz. Yaygın olarak kullanılan kural aşağıda verilmiştir:

- *. props* dosyaları içeri aktarma sırasında erken içeri aktarılır.

- *. targets*  dosyaları, derleme sırasında geç alınır.

Bu kural `<Project Sdk="SdkName">` içeri aktarmalar tarafından zorlanır (yani, *SDK. props* 'ın içe aktarılması ilk olarak, dosyanın tüm içeriğiyle önce gelir ve ardından *SDK. targets* , dosyanın tüm içeriğinden sonra, son olarak gelir.

Özellikleri yerleştireceğiniz yere karar verirken aşağıdaki genel yönergeleri kullanın:

- Birçok özellik için nerede tanımlandıklarından bağımsız değildir, çünkü üzerine yazılmazlar ve yalnızca yürütme sırasında okunacaktır.

- Tek bir projede özelleştirilebilen olabilecek davranış için, varsayılan olarak *. props* dosyaları ayarlayın.

- Özelleştirilmiş bir özelliğin değerini okuyarak *. props* dosyalarında bağımlı özellikleri ayarlamaktan kaçının, çünkü MSBuild Kullanıcı projesini okuuncaya kadar özelleştirme gerçekleşmez.

- Her bir projeden özelleştirmeler sunduklarında, *. targets* dosyalarında bağımlı özellikleri ayarlayın.

- Özellikleri geçersiz kılmanız gerekirse, tüm Kullanıcı-proje özelleştirmeleri yürürlüğe girdikten sonra bir *. targets* dosyasında bunu yapın. Türetilmiş özellikleri kullanırken dikkatli olun; türetilmiş özelliklerin de geçersiz kılınması gerekebilir.

- Öğeleri *. props* dosyalarına ekleyin (bir özelliğe koşullu). Tüm özellikler herhangi bir öğeden önce değerlendirilir, bu nedenle kullanıcı-proje özellik özelleştirmeleri çekilir ve bu, kullanıcının projesine `Remove` veya `Update` içeri aktarma tarafından alınan herhangi bir öğeye sahip olmasını sağlar.

- *. Targets* dosyalarındaki hedefleri tanımlayın. Ancak, *. targets* dosyası bir SDK tarafından içeri aktarılmışsa, bu senaryonun, Kullanıcı projesinin varsayılan olarak geçersiz kılmak için bir yeri olmadığından, hedefin geçersiz kılmayı daha zor hale getirmeyi unutmayın.

- Mümkünse, hedef içindeki özellikleri değiştirmek için değerlendirme sırasında özellikleri özelleştirmeyi tercih edin. Bu kılavuz, bir projeyi yüklemeyi ve ne yaptığını anlamayı kolaylaştırır.

## <a name="msbuildprojectextensionspath"></a>Msbuildprojeclarsionspath

Varsayılan olarak, *Microsoft. Common. props* içeri aktarmaları `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` ve *Microsoft. Common. targets* içeri aktarmaları `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets` . Varsayılan değeri `MSBuildProjectExtensionsPath` `$(BaseIntermediateOutputPath)` , olur `obj/` . NuGet, paketlerle birlikte sunulan derleme mantığına başvurmak için bu mekanizmayı kullanır; diğer bir deyişle, geri yükleme sırasında `{project}.nuget.g.props` paket içeriğine başvuran dosyalar oluşturulur.

Özelliğini `ImportProjectExtensionProps` `false` bir *Dizin. Build. props* veya *Microsoft. Common. props*içeri aktarmadan önce bir dizinde ayarlayarak bu genişletilebilirlik mekanizmasını devre dışı bırakabilirsiniz.

> [!NOTE]
> Msbuildprojecyısionspath içeri aktarmaları devre dışı bırakıldığında, NuGet paketlerinde verilen derleme mantığı projenize uygulanmasını engeller. Bazı NuGet paketleri işlevlerini gerçekleştirmek için derleme mantığı gerektirir ve bu devre dışı bırakıldığında kullanılamaz hale alınacaktır.

## <a name="user-file"></a>. Kullanıcı dosyası

*Microsoft. Common. CurrentVersion. targets* , varsa içeri aktarılır `$(MSBuildProjectFullPath).user` . bu nedenle, bu ek uzantı ile projenizin yanına bir dosya oluşturabilirsiniz. Kaynak denetimi iade yapmayı planladığınız uzun süreli değişiklikler için, gelecekteki bakım yapanlar bu uzantı mekanizması hakkında bilgi sahibi olmak zorunda kalmayacak şekilde projenin kendisini değiştirmeyi tercih edersiniz.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath ve MSBuildUserExtensionsPath

> [!WARNING]
> Bu uzantı mekanizmalarının kullanılması, makineler arasında tekrarlanabilir derlemeler almanızı zorlaştırır. Kaynak denetim sisteminize denetlenebildiği ve kod tabanınızın tüm geliştiricileri arasında paylaşılan bir yapılandırma kullanmayı deneyin.

Kurala göre, birçok çekirdek derleme mantığı dosyası içeri aktarır

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

içeriğinden önce ve

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

ardından. Bu kural, yüklü SDK 'ların ortak proje türlerinin derleme mantığını belirlemesine izin verir.

Aynı dizin yapısı, `$(MSBuildUserExtensionsPath)` Kullanıcı başına *%LocalAppData%\microsoft\msbuild*olan ' de arama yapılır. Bu klasöre yerleştirilmiş dosyalar, ilgili proje türünün tüm derlemeleri için kullanıcının kimlik bilgileri altında çalıştırılacaktır. Düzendeki içeri aktarma dosyasından sonra adlı özellikleri ayarlayarak Kullanıcı uzantılarını devre dışı bırakabilirsiniz `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` . Örneğin, olarak ayarlanması `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` `false` içeri aktarmayı engeller `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` .

## <a name="customize-the-solution-build"></a>Çözüm derlemesini özelleştirme

> [!IMPORTANT]
> Çözüm derlemesini bu şekilde özelleştirmek yalnızca *MSBuild.exe*olan komut satırı derlemeleri için geçerlidir. Visual Studio içindeki derlemeler **için geçerlidir.** Bu nedenle, özelleştirmenin çözüm düzeyine konulmasının kullanılması önerilmez. Bir Çözümdeki tüm projelerin özelleştirilmesi için daha iyi bir alternatif, bu makalenin başka bir yerinde anlatıldığı gibi çözüm klasöründe *Dizin. Build. props* ve *Directory. Build. targets* dosyalarını kullanmaktır.

MSBuild bir çözüm dosyası oluşturduğunda, önce onu bir proje dosyasına dönüştürür ve ardından bunu oluşturur. Oluşturulan proje dosyası, `before.{solutionname}.sln.targets` `after.{solutionname}.sln.targets` ve dizinlerine yüklenmiş hedefler de dahil olmak üzere herhangi bir hedefi tanımlamadan önce ve hedefleri içeri aktardıktan sonra içeri aktarılır `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` .

Örneğin, daha sonra adlı aynı dizinde bir dosya oluşturarak *MyCustomizedSolution. sln* derlemeden sonra özel bir günlük iletisi yazmak üzere yeni bir hedef tanımlayabilirsiniz *. Şunu içeren MyCustomizedSolution. sln. targets*

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

Çözüm derlemesi proje Derlemeleriyle ayrıdır, bu nedenle buradaki ayarlar proje derlemelerini etkilemez.

## <a name="customize-all-net-builds"></a>Tüm .NET derlemelerini özelleştirin

Bir yapı sunucusu korunurken, sunucudaki tüm derlemeler için MSBuild ayarlarını küresel olarak yapılandırmanız gerekebilir.  Prensibi, genel *Microsoft. Common. targets* veya *Microsoft. Common. props* dosyalarını değiştirebilir, ancak daha iyi bir yoldur. Belirli bir proje türünün (tüm C# projeleri gibi) tüm yapılarını, belirli MSBuild özelliklerini kullanarak ve belirli özel ve dosyaları ekleyerek etkileyebilirsiniz `.targets` `.props` .

MSBuild veya Visual Studio 'nun bir yüklemesiyle yönetilen tüm C# veya Visual Basic yapılarını etkilemek için özel bir dosya oluşturun. *Microsoft. Common. targets* veya *Custom. After. Microsoft. Common.* targets, *Microsoft. Common. targets*ya da bir dosya *Custom* . before. Microsoft. Common. props ya da özel *. After. Microsoft. Common. props* , *Microsoft. Common. props*'dan önce veya sonra işlenecek özelliklerle birlikte çalışır.

Aşağıdaki MSBuild özelliklerini kullanarak bu dosyaların konumlarını belirtebilirsiniz:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Bu özelliklerin *ortak* sürümleri hem C# hem de Visual Basic projelerini etkiler. Bu özellikleri MSBuild komut satırında ayarlayabilirsiniz.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

En iyi yaklaşım senaryonuza bağlıdır. Visual Studio genişletilebilirliği kullanarak, yapı sistemini özelleştirebilir ve özelleştirmeleri yükleme ve yönetmeye yönelik bir mekanizma sağlayabilirsiniz.

Adanmış bir yapı sunucunuz varsa ve belirli hedeflerin bu sunucuda yürütülen uygun proje türünün tüm yapılarında her zaman yürütülememesini sağlamak istiyorsanız, genel bir özel `.targets` veya `.props` dosya kullanmak mantıklı olur.  Özel hedeflerin yalnızca belirli koşullar geçerli olduğunda yürütmesini istiyorsanız, başka bir dosya konumu kullanın ve MSBuild komut satırındaki uygun MSBuild özelliğini yalnızca gerektiğinde ayarlayarak bu dosyanın yolunu ayarlayın.

> [!WARNING]
> Visual Studio, `.targets` `.props` eşleşen türün herhangi bir projesini her oluşturduğunda MSBuild klasöründe bulursa, özel veya dosyaları kullanır. Bu, istenmeyen sonuçlara neden olabilir ve yanlış yapıldıysa, Visual Studio 'nun bilgisayarınızda derleme yeteneğini devre dışı bırakabilir.

## <a name="customize-c-builds"></a>C++ derlemelerini özelleştirme

C++ projeleri için, daha önce bahsedilen özel *. targets* ve *. props* dosyaları varsayılan ayarları geçersiz kılmak için aynı şekilde kullanılamaz. *Directory. Build. props* , Microsoft tarafından içeri aktarılır. varsayılan olarak ' de Içeri aktarılan *ortak. props*, `Microsoft.Cpp.Default.props` *Microsoft. cpp. props* içinde tanımlanmıştır ve bir dizi özellik için, özelliği zaten tanımlandığından, varsayılan olarak, içinde tanımlanan belirli proje özellikleri için farklı olması gerekir `PropertyGroup` `Label="Configuration"` (bkz [. vcxproj ve. props dosya yapısı](/cpp/build/reference/vcxproj-file-structure)).

Ancak, *Microsoft. cpp. \* * Files 'dan önce/sonra otomatik olarak içeri aktarılacak *. props* dosyalarını belirtmek için aşağıdaki özellikleri kullanabilirsiniz:

- Forceımportaftercppdefaultprops
- ForceImportBeforeCppProps
- Forceımportaftercppprops
- ForceImportBeforeCppTargets
- Forceımportaftercpptargets

Tüm C++ Derlemeleriyle ilgili özelliklerin varsayılan değerlerini özelleştirmek için, başka bir *. props* dosyası (deyin, *MyProps. props*) oluşturun ve `ForceImportAfterCppProps` `Directory.Build.props` bunu işaret eden özelliği tanımlayın:

<PropertyGroup><ForceImportAfterCppProps>$ (Msbuildthisfiledirectory) \Myprops.exe<ForceImportAfterCppProps>
</PropertyGroup>

*MyProps. props* , *Microsoft. cpp. props*'un en sonunda otomatik olarak içeri aktarılacaktır.

## <a name="customize-all-c-builds"></a>Tüm C++ derlemelerini özelleştirin

Visual Studio yüklemesinin özelleştirilmesi önerilmez, çünkü bu tür özelleştirmeleri izlemek kolaydır, ancak Visual Studio 'Yu belirli bir platform için C++ derlemelerini özelleştirmek üzere uzatdıysanız, `.targets` her platform için dosya oluşturabilir ve bunları bir Visual Studio uzantısının parçası olarak bu platformlar için uygun içeri aktarma klasörlerine yerleştirebilirsiniz.

`.targets` *Microsoft. cpp. Win32. targets*Win32 platformunun dosyası aşağıdaki `Import` öğeyi içerir:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Aynı dosyanın ucunun yakınında benzer bir öğe vardır:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

*%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {Version} \ platformlarındaki diğer hedef platformlar için benzer içeri aktarma öğeleri var \* .

`.targets`Dosyayı `ImportAfter` platforma göre uygun klasöre yerleştirdiğinizde, MSBuild dosyanızı bu platform Için her C++ derlemesine içeri aktarır. Gerekirse, birden çok `.targets` Dosya koyabilirsiniz. 

Visual Studio genişletilebilirliği kullanarak, yeni bir platform tanımlama gibi daha fazla özelleştirme mümkündür. Daha fazla bilgi için bkz. [C++ proje genişletilebilirliği](../extensibility/visual-cpp-project-extensibility.md).

### <a name="specify-a-custom-import-on-the-command-line"></a>Komut satırında özel bir içeri aktarma belirtin

`.targets`C++ projesinin belirli bir derlemesi için eklemek istediğiniz özel için, özelliklerden birini veya her ikisini de `ForceImportBeforeCppTargets` ve `ForceImportAfterCppTargets` komut satırını ayarlayın.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Genel bir ayar (bir yapı sunucusundaki bir platform için tüm C++ derlemelerini etkilemek, söylemek amacıyla) için iki yöntem vardır. İlk olarak, bu özellikleri her zaman ayarlanmış bir sistem ortam değişkeni kullanarak ayarlayabilirsiniz. Bu, MSBuild her zaman ortamı okuduğundan ve tüm ortam değişkenlerine yönelik özellikler oluşturduğunda (veya geçersiz kılındığından), bu işe yarar.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
