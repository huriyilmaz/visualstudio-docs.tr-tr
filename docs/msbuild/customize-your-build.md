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
ms.openlocfilehash: 4f1b0e774d70c5787a7221aa0dfa7b0834dac7e3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588297"
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

Örneğin, tüm projelerinizi yeni Roslyn **/belirleyici** özelliğine erişecek şekilde etkinleştirmek isterseniz (Bu, özellik `$(Deterministic)`tarafından roslyn `CoreCompile` hedefinde sunulur), aşağıdakileri yapabilirsiniz.

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

Bir *Dizin. Build. props* dosyası ararken, MSBuild, dizin yapısını proje konumınızdan (`$(MSBuildProjectFullPath)`) yukarı doğru bir şekilde gösterir. bir dizin bulduktan sonra durduruluyor. *Build. props* dosyası. Örneğin, `$(MSBuildProjectFullPath)` *c:\users\username\code\test\case1*ise, MSBuild orada aramaya başlar ve ardından dizin yapısını bir *Dizin. Build. props* dosyası bulana kadar yukarı doğru arama sırasında aşağıdaki dizin yapısında bulunur.

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

*Dizin. Build. targets* , NuGet paketlerindeki *. targets* dosyalarını içeri aktardıktan sonra *Microsoft. Common. targets* 'dan içeri aktarılır. Bu nedenle, derleme mantığının çoğunda tanımlanan özellikleri ve hedefleri geçersiz kılabilir, ancak bazen son içeri aktarma işleminden sonra proje dosyasını özelleştirmeniz gerekebilir.

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
- Birden çok düzeyin bulunmasını ve birleştirilmesini istiyorsanız, "iç" dosyadan "dış" dosya [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (yukarıda gösterilen)
- "Dış" dosya kendisine ait bir şeyi de içeri aktarmadıysanız, tarama bunu durdur
- Tarama/birleştirme işlemini denetlemek için `$(DirectoryBuildPropsPath)` ve `$(ImportDirectoryBuildProps)` kullanın

Ya da daha fazla: herhangi bir şeyi içeri aktarmaz ilk *Dizin. Build. props* , MSBuild 'in durduğu yerdir.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Bir. props veya. targets dosyasına özellik ekleme arasında seçim yapın

MSBuild içeri aktarma-sipariş bağımlıdır ve bir özelliğin (ya da bir `UsingTask` ya da hedefin) son tanımı kullanılan tanımdır.

Açık içeri aktarmalar kullanılırken, herhangi bir noktada bir *. props* veya *. targets* dosyasından içeri aktarabilirsiniz. Yaygın olarak kullanılan kural aşağıda verilmiştir:

- *. props* dosyaları içeri aktarma sırasında erken içeri aktarılır.

- *. targets* dosyaları, derleme sırasında geç alınır.

Bu kural, `<Project Sdk="SdkName">` içeri aktarmalar tarafından zorlanır (diğer bir deyişle, *SDK. props* 'ın içe aktarılması ilk olarak, dosyanın tüm içeriğiyle önce gelir ve ardından *SDK. targets* , dosyanın tüm içeriğinden sonra, son olarak gelir.)

Özellikleri yerleştireceğiniz yere karar verirken aşağıdaki genel yönergeleri kullanın:

- Birçok özellik için nerede tanımlandıklarından bağımsız değildir, çünkü üzerine yazılmazlar ve yalnızca yürütme sırasında okunacaktır.

- Tek bir projede özelleştirilebilen olabilecek davranış için, varsayılan olarak *. props* dosyaları ayarlayın.

- Özelleştirilmiş bir özelliğin değerini okuyarak *. props* dosyalarında bağımlı özellikleri ayarlamaktan kaçının, çünkü MSBuild Kullanıcı projesini okuuncaya kadar özelleştirme gerçekleşmez.

- Her bir projeden özelleştirmeler sunduklarında, *. targets* dosyalarında bağımlı özellikleri ayarlayın.

- Özellikleri geçersiz kılmanız gerekirse, tüm Kullanıcı-proje özelleştirmeleri yürürlüğe girdikten sonra bir *. targets* dosyasında bunu yapın. Türetilmiş özellikleri kullanırken dikkatli olun; türetilmiş özelliklerin de geçersiz kılınması gerekebilir.

- Öğeleri *. props* dosyalarına ekleyin (bir özelliğe koşullu). Tüm özellikler herhangi bir öğeden önce değerlendirilir, bu nedenle kullanıcı-proje özellik özelleştirmeleri çekilir ve bu, kullanıcının projesine içeri aktarma tarafından alınan herhangi bir öğeyi `Remove` veya `Update` fırsatı verir.

- *. Targets* dosyalarındaki hedefleri tanımlayın. Ancak, *. targets* dosyası bir SDK tarafından içeri aktarılmışsa, bu senaryonun, Kullanıcı projesinin varsayılan olarak geçersiz kılmak için bir yeri olmadığından, hedefin geçersiz kılmayı daha zor hale getirmeyi unutmayın.

- Mümkünse, hedef içindeki özellikleri değiştirmek için değerlendirme sırasında özellikleri özelleştirmeyi tercih edin. Bu kılavuz, bir projeyi yüklemeyi ve ne yaptığını anlamayı kolaylaştırır.

## <a name="msbuildprojectextensionspath"></a>Msbuildprojeclarsionspath

Varsayılan olarak, *Microsoft. Common. props* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` ve *Microsoft. Common. targets* içeri aktarmalar `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. `MSBuildProjectExtensionsPath` varsayılan değeri `$(BaseIntermediateOutputPath)``obj/`. NuGet, paketlerle birlikte sunulan derleme mantığına başvurmak için bu mekanizmayı kullanır; diğer bir deyişle, geri yükleme sırasında paket içeriğine başvuran `{project}.nuget.g.props` dosyaları oluşturur.

Özellik `ImportProjectExtensionProps` bir dizinde `false` olarak ayarlayarak bu genişletilebilirlik mekanizmasını devre dışı bırakabilirsiniz *. Build. props* veya *Microsoft. Common. props*içeri aktarmadan önce.

> [!NOTE]
> Msbuildprojecyısionspath içeri aktarmaları devre dışı bırakıldığında, NuGet paketlerinde verilen derleme mantığı projenize uygulanmasını engeller. Bazı NuGet paketleri işlevlerini gerçekleştirmek için derleme mantığı gerektirir ve bu devre dışı bırakıldığında kullanılamaz hale alınacaktır.

## <a name="user-file"></a>. Kullanıcı dosyası

*Microsoft. Common. CurrentVersion. targets* , varsa `$(MSBuildProjectFullPath).user` içeri aktarır. böylece, bu ek uzantı ile projenizin yanına bir dosya oluşturabilirsiniz. Kaynak denetimi iade yapmayı planladığınız uzun süreli değişiklikler için, gelecekteki bakım yapanlar bu uzantı mekanizması hakkında bilgi sahibi olmak zorunda kalmayacak şekilde projenin kendisini değiştirmeyi tercih edersiniz.

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

Aynı dizin yapısı, Kullanıcı başına *%LocalAppData%\microsoft\msbuild*olan `$(MSBuildUserExtensionsPath)`' de aranır. Bu klasöre yerleştirilmiş dosyalar, ilgili proje türünün tüm derlemeleri için kullanıcının kimlik bilgileri altında çalıştırılacaktır. Model `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`içeri aktarma dosyasından sonra adlı özellikleri ayarlayarak Kullanıcı uzantılarını devre dışı bırakabilirsiniz. Örneğin, `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` `false` ayarlanması `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`içeri aktarmayı engeller.

## <a name="customize-the-solution-build"></a>Çözüm derlemesini özelleştirme

> [!IMPORTANT]
> Çözüm derlemesini bu şekilde özelleştirmek, yalnızca *MSBuild. exe*ile komut satırı derlemeleri için geçerlidir. Visual Studio içindeki derlemeler **için geçerlidir.**

MSBuild bir çözüm dosyası oluşturduğunda, önce onu bir proje dosyasına dönüştürür ve ardından bunu oluşturur. Oluşturulan proje dosyası, `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` ve `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` dizinlerine yüklenmiş hedefler dahil olmak üzere hedefleri ve `after.{solutionname}.sln.targets` almadan önce `before.{solutionname}.sln.targets` içeri aktarır.

Örneğin, daha sonra adlı aynı dizinde bir dosya oluşturarak *MyCustomizedSolution. sln* derlemeden sonra özel bir günlük iletisi yazmak üzere yeni bir hedef tanımlayabilirsiniz *. Şunu içeren MyCustomizedSolution. sln. targets*

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
