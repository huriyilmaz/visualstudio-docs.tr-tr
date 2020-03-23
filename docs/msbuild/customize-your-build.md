---
title: Yapınızı özelleştirin | Microsoft Dokümanlar
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
ms.openlocfilehash: e7ddf87f5fa9f937c0272e37f3a6b4aba29f2d6c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652800"
---
# <a name="customize-your-build"></a>Derlemenizi özelleştirme

Standart yapı işlemini kullanan MSBuild projeleri *(Microsoft.Common.props* ve *Microsoft.Common.targets*alma) yapı işleminizi özelleştirmek için kullanabileceğiniz birkaç genişletilebilirlik kancasına sahiptir.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Projeniz için komut satırı MSBuild çağrılarına bağımsız değişkenler ekleme

Kaynak dizininizin içinde veya üstündeki *bir Directory.Build.rsp* dosyası, projenizin komut satırı yapılarına uygulanır. Ayrıntılar için [MSBuild yanıt dosyalarına](../msbuild/msbuild-response-files.md#directorybuildrsp)bakın.

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props ve Directory.Build.targets

MSBuild sürüm 15'ten önce, çözümünüzdeki projelere yeni, özel bir özellik sağlamak istiyorsanız, çözümdeki her proje dosyasına bu özelliğe el ile bir başvuru eklemeniz gerekiyordu. Veya, özelliği bir *.props* dosyasında tanımlamanız ve diğer şeylerin yanı sıra çözümdeki her projede *.props* dosyasını açıkça içe aktarmanız gerekiyordu.

Ancak, artık her projeye tek adımda yeni bir özellik ekleyebilirsiniz, kaynağınızı içeren kök klasöründe *Directory.Build.props* adlı tek bir dosyada tanımlayabilirsiniz. MSBuild çalıştığında, *Microsoft.Common.props* *Dizin.Build.props* dosyası için dizin yapınızı arar (ve *Microsoft.Common.targets* *Directory.Build.targets'ı*arar). Eğer bir tane bulursa, mülkü ithal etmek. *Directory.Build.props,* bir dizin altındaki projelere özelleştirmeler sağlayan kullanıcı tanımlı bir dosyadır.

> [!NOTE]
> Linux tabanlı dosya sistemleri büyük/küçük harf duyarlıdır. Directory.Build.props dosya adının kasasının tam olarak eşleştiğinden emin olun, yoksa yapı işlemi sırasında algılanmayacak.
>
> Daha fazla bilgi için [bu GitHub sorununa](https://github.com/dotnet/core/issues/1991#issue-368441031) bakın.

### <a name="directorybuildprops-example"></a>Directory.Build.props örneği

Örneğin, tüm projelerinizin yeni Roslyn/deterministik **/deterministic** özelliğe erişmesini sağlamak istiyorsanız (özellik `$(Deterministic)`tarafından `CoreCompile` Roslyn hedefinde açıkta dır), aşağıdakileri yapabilirsiniz.

1. Repo'nuzun kökünde *Directory.Build.props*adlı yeni bir dosya oluşturun.
2. Aşağıdaki XML'yi dosyaya ekleyin.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. MSBuild çalıştırın. Projenizin *Microsoft.Common.props* ve *Microsoft.Common.targets'in* varolan içe aktarışları dosyayı bulun ve içe aktarıyor.

### <a name="search-scope"></a>Arama kapsamı

*Bir Dizin.Build.props* dosyasını ararken, MSBuild dizin yapısını proje`$(MSBuildProjectFullPath)`konumunuzdan yukarı doğru yürür ( ), *dizin.Build.prop* dosyasını buladıktan sonra durur. Örneğin, `$(MSBuildProjectFullPath)` *c:\users\username\code\test\case1*ise, MSBuild burada arama yapmaya başlar ve ardından aşağıdaki dizin yapısında olduğu gibi bir *Dizin.Build.props* dosyası bulunana kadar dizin yapısını yukarı doğru arar.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Çözüm dosyasının konumu *Directory.Build.props*ile alakasızdır.

### <a name="import-order"></a>İthalat siparişi

*Directory.Build.props* *Microsoft.Common.props*çok erken alınır ve özellikleri daha sonra tanımlanan kullanılamaz. Bu nedenle, henüz tanımlanmamış (ve boşalmak için değerlendirecek) özelliklere atıfta kullanmaktan kaçının.

*Directory.Build.targets,* NuGet paketlerinden *.targets* dosyalarını aldıktan sonra *Microsoft.Common.targets'tan* alınır. Bu nedenle, yapı mantığının çoğunda tanımlanan özellikleri ve hedefleri geçersiz kılabilir, ancak bazen son alma işleminden sonra proje dosyasını özelleştirmeniz gerekebilir.

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

Tüm projeler *(1)* için ortak özelliklere, *src* projeleri için ortak özelliklere *(2-src)* ve *test* projeleri *(2-test)* için ortak özelliklere sahip olmak istenebilir.

MSBuild doğru "iç" dosyaları birleştirmek yapmak için *(2-src* ve *2-test*) "dış" dosya (*1),* bir kez MSBuild bir *Directory.Build.props* dosyası bulur dikkate almak gerekir, daha fazla tarama durur. Taramaya devam etmek ve dış dosyada birleştirmek için bu kodu her iki iç dosyaya da yerleştirin:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild genel yaklaşımının bir özeti aşağıdaki gibidir:

- Herhangi bir proje için, MSBuild çözüm yapısında yukarı doğru ilk *Directory.Build.prop* bulur, varsayılanlar ile birleştirir ve daha fazla tarama durur
- Birden çok düzeyin bulunmasını ve birleştirilmesini istiyorsanız, "iç" [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) dosyadaki "dış" dosya (yukarıda gösterilmiştir)
- "Dış" dosya nın kendisi de üzerinde bir şey almak değilse, o zaman tarama orada durur
- Tarama/birleştirme işlemini kontrol etmek `$(DirectoryBuildPropsPath)` için,`$(ImportDirectoryBuildProps)`

Ya da daha basit: hiçbir şey almaz ilk *Directory.Build.props* MSBuild durur nerede.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>.props veya .targets dosyasına özellik ekleme arasında seçim yapma

MSBuild alma siparişine bağlıdır ve bir özelliğin `UsingTask` (veya bir veya hedefin) son tanımı kullanılan tanımdır.

Açık içeri alma kullanırken, herhangi bir noktada *.props* veya *.targets* dosyasından içe aktarabilirsiniz. Burada yaygın olarak kullanılan kongre:

- *.props* dosyaları alma siparişinin erken saatlerinde alınır.

- *.targets* dosyaları yapı siparişinin sonlarına doğru alınır.

Bu sözleşme, `<Project Sdk="SdkName">` içe aktarma tarafından uygulanır (diğer bir şekilde, *Sdk.props'un* içe aktarımı önce gelir, dosyanın tüm içeriğinden önce, sonra *Sdk.targets* dosyanın tüm içeriğinden sonra son gelir).

Özellikleri nereye koyacağına karar verirken aşağıdaki genel yönergeleri kullanın:

- Birçok özellik için, nerede tanımlandığı önemli değildir, çünkü bunlar üzerine yazılmadıkları ve yalnızca yürütme zamanında okunacak.

- Tek bir projede özelleştirilebilen davranışlar için varsayılanları *.props* dosyalarında ayarlayın.

- MSBuild kullanıcının projesini okuyana kadar özelleştirme gerçekleşmeyeceğinden, özelleştirilmiş bir özelliğin değerini okuyarak *.prop* s dosyalarına bağımlı özellikler ayarlamaktan kaçının.

- Tek tek projelerden özelleştirmeler alacakları için *.targets* dosyalarına bağımlı özellikleri ayarlayın.

- Özellikleri geçersiz kılmanız gerekiyorsa, tüm kullanıcı projesi özelleştirmeleri etkili olma şansına sahip olduktan sonra bunu *bir .targets* dosyasında yapın. Türetilmiş özellikleri kullanırken dikkatli olun; türetilen özellikleride de geçersiz kılınması gerekebilir.

- Öğeleri *.props* dosyalarına (özellik üzerinde koşullandırılmış) ekleyin. Tüm özellikler herhangi bir öğeden önce kabul edilir, bu nedenle kullanıcı-proje özellik özelleştirmeleri `Remove` `Update` alınır ve bu kullanıcının projesine alma veya alma tarafından getirilen herhangi bir öğeye fırsat verir.

- Hedefleri .targets dosyalarında *tanımlayın.* Ancak, *.targets* dosyası bir SDK tarafından içe aktarılırsa, kullanıcının projesivarsayılan olarak geçersiz kılacak bir yeri olmadığından, bu senaryonun hedefi geçersiz kılmayı daha zor hale getirir.

- Mümkünse, bir hedef içindeki özellikleri değiştirmeye göre değerlendirme zamanında özellikleri özelleştirmeyi tercih edin. Bu kılavuz, bir projeyi yüklemeyi ve ne yaptığını anlamayı kolaylaştırır.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Varsayılan olarak, *Microsoft.Common.props* içeri `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` aktarımları `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`ve *Microsoft.Common.targets* içeri aktarımları. Varsayılan değeri `MSBuildProjectExtensionsPath` `$(BaseIntermediateOutputPath)`, `obj/`. NuGet, paketlerle teslim edilen mantık oluşturmak için bu mekanizmayı kullanır; diğer bir zamanda, paket içeriğine başvuran `{project}.nuget.g.props` dosyalar oluşturur.

`ImportProjectExtensionProps` Bu genişletilebilirlik mekanizmasını, özelliği bir `false` *Dizin.Build.prop'a* veya *Microsoft.Common.props'a*aktarmadan önce ayarlayarak devre dışı kullanabilirsiniz.

> [!NOTE]
> MSBuildProjectExtensionsPath içeri aktarımlarının devre dışı bırakılması, NuGet paketlerinde teslim edilen yapı mantığının projenize uygulanmasını önler. Bazı NuGet paketleri işlevlerini gerçekleştirmek için yapı mantığı gerektirir ve bu devre dışı bırakıldığında işe yaramaz hale getirilir.

## <a name="user-file"></a>.user dosyası

*Microsoft.Common.CurrentVersion.targets* `$(MSBuildProjectFullPath).user` varsa içeri alma, böylece bu ek uzantı ile projenizin yanında bir dosya oluşturabilirsiniz. Uzun vadeli değişiklikler için kaynak denetimine giriş yapmayı planlıyorsunuz, gelecekteki bakımcıların bu uzantı mekanizması hakkında bilgi sahibi olmak zorunda kalmaması için projenin kendisini değiştirmeyi tercih edersiniz.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath ve MSBuildUserExtensionsPath

> [!WARNING]
> Bu uzantı mekanizmalarının kullanılması, makineler arasında tekrarlanabilir yapılar elde etmeyi zorlaştırır. Kaynak denetim sisteminizde denetlenebilir ve kod tabanınızın tüm geliştiricileri arasında paylaşılabilen bir yapılandırma kullanmaya çalışın.

Sözleşmeye göre, birçok çekirdek oluşturma mantık dosyaları alma

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

içeriklerinden önce ve

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

Sonra. Bu kural, yüklü SDK'ların ortak proje türlerinin yapı mantığını genişletmesine olanak tanır.

Aynı dizin `$(MSBuildUserExtensionsPath)`yapısı, kullanıcı başına klasör *%LOCALAPPDATA%\Microsoft\MSBuild*olan için aranır. Bu klasöre yerleştirilen dosyalar, bu kullanıcının kimlik bilgileri altında çalıştırılan ilgili proje türündeki tüm yapılar için alınır. Desende `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`içe aktarma dosyasının adını taşıyan özellikleri ayarlayarak kullanıcı uzantılarını devre dışı kullanabilirsiniz. Örneğin, alma'yı `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` `false` `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`engelleyecek ayarı.

## <a name="customize-the-solution-build"></a>Çözüm oluşturmayı özelleştirin

> [!IMPORTANT]
> Bu şekilde çözüm oluşturmak özelleştirme sadece *MSBuild.exe*ile komut satırı yapılar için geçerlidir. Visual Studio içinde inşa için geçerli **değildir.**

MSBuild bir çözüm dosyası oluşturduğunda, önce bir proje dosyasına dahili olarak çevirir ve sonra bunu oluşturur. Oluşturulan proje dosyası, herhangi bir `before.{solutionname}.sln.targets` `after.{solutionname}.sln.targets` hedefi tanımlamadan önce ve hedeflere ve `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` dizinlere yüklenen hedefler de dahil olmak üzere hedefleri aldıktan sonra içe aktarılır.

Örneğin, *MyCustomizedSolution.sln'yi* oluşturduktan sonra, adlandırılmış aynı dizinde bir dosya oluşturarak özel bir günlük iletisi yazmak için yeni bir hedef *tanımlayabilirsiniz. MyCustomizedSolution.sln.targets* içeren

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="customize-all-net-builds"></a>Tüm .NET yapılarını özelleştirin

Bir yapı sunucusu tutarken, sunucudaki tüm yapılar için MSBuild ayarlarını genel olarak yapılandırmanız gerekebilir.  Prensip olarak, global *Microsoft.Common.Targets* veya *Microsoft.Common.Props* dosyalarını değiştirebilirsiniz, ancak daha iyi bir yol vardır. Belirli MSBuild özelliklerini kullanarak ve belirli özel `.targets` ve `.props` dosyalar ekleyerek belirli bir proje türünün tüm yapılarını (tüm C# projeleri gibi) etkileyebilirsiniz.

MSBuild veya Visual Studio'nun kurulumu tarafından yönetilen tüm C# veya Visual Basic yapılarını etkilemek için *Custom.Before.Before.Microsoft.Common.Targets* veya *Custom.After.Microsoft.Common.Targets* veya *Custom.Before.Before.Common.Props* veya *Custom.After.Microsoft.Common.Props* adresinde veya *Microsoft.Common.prop'dan*önce veya sonra işlenecek özelliklere sahip bir dosya oluşturun. *Microsoft.Common.targets*

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

En iyi yaklaşım senaryonuza bağlıdır. Özel bir yapı sunucunuz varsa ve belirli hedeflerin her zaman bu sunucuda çalışan uygun proje türünün `.targets` tüm `.props` yapılarında yürütülmesini sağlamak istiyorsanız, genel bir özel veya dosya kullanmak mantıklıdır.  Özel hedeflerin yalnızca belirli koşullar uygulandığında yürütülmesini istiyorsanız, başka bir dosya konumu kullanın ve yalnızca gerektiğinde MSBuild komut satırında uygun MSBuild özelliğini ayarlayarak bu dosyanın yolunu ayarlayın.

> [!WARNING]
> Visual Studio, `.targets` eşleşen `.props` türde herhangi bir proje oluşturduğunda MSBuild klasöründe bulursa özel dosyaları veya dosyaları kullanır. Bu istenmeyen sonuçlara yol açabilir ve yanlış yapılırsa, Visual Studio'nun bilgisayarınızda oluşturma yeteneğini devre dışı kılabilir.

## <a name="customize-all-c-builds"></a>Tüm C++ yapılarını özelleştirin

C++ projeleri için, daha önce `.targets` `.props` bahsedilen özel ve dosyalar yoksayılır. C++ projeleri için, `.targets` her platform için dosya oluşturabilir ve bunları bu platformlar için uygun alma klasörlerine yerleştirebilirsiniz.

Win32 platformu, *Microsoft.Cpp.Win32.targets*için `.targets` dosya, `Import` aşağıdaki öğeyi içerir:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Aynı dosyanın sonuna yakın benzer bir öğe var:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Benzer alma öğeleri *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platformlar'daki\*diğer hedef platformlar için de vardır.

Dosyayı `.targets` platforma göre uygun klasöre yerleştirdikten sonra, MSBuild dosyanızı o platform için yapılan her C++ yapısına aktarabilir. Gerekirse oraya `.targets` birden çok dosya koyabilirsiniz.

### <a name="specify-a-custom-import-on-the-command-line"></a>Komut satırında özel bir alma belirtin

Bir `.targets` C++ projesinin belirli bir yapısı için eklemek istediğiniz özel için, `ForceImportBeforeCppTargets` `ForceImportAfterCppTargets` özelliklerden birini veya her ikisini de komut satırına ayarlayın.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Genel bir ayar için (örneğin, tüm C++ bir yapı sunucusunda bir platform oluşturur) iki yöntem vardır. İlk olarak, bu özellikleri her zaman ayarlanmış bir sistem ortamı değişkenini kullanarak ayarlayabilirsiniz. MSBuild her zaman ortamı okuduğundan ve tüm ortam değişkenleri için özellikler oluşturduğundan (veya geçersiz kılar) bu işe yarar.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
