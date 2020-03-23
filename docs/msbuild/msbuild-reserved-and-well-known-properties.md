---
title: MSBuild Saklıdır ve Tanınmış Özellikleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10b38ca4bfc0ea8a326f015228a4152779a41650
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633258"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild ayrılmış ve iyi bilinen özellikleri

MSBuild, proje dosyası ve MSBuild ikilileri hakkında bilgi depolayan bir dizi önceden tanımlanmış özellik sağlar. Bu özellikler, diğer MSBuild özellikleriyle aynı şekilde değerlendirilir. Örneğin, `MSBuildProjectFile` özelliği kullanmak için, `$(MSBuildProjectFile)`yazın.

 MSBuild, ayrılmış ve iyi bilinen özellikleri önceden tanımlamak için aşağıdaki tablodaki değerleri kullanır. Ayrılmış özellikler geçersiz kılınamaz, ancak iyi bilinen özellikler, proje dosyasında bildirilen aynı adlandırılmış ortam özellikleri, genel özellikler veya özellikler kullanılarak geçersiz kılınabilir.

## <a name="reserved-and-well-known-properties"></a>Ayrılmış ve iyi bilinen özellikler

 Aşağıdaki tabloda MSBuild önceden tanımlanmış özellikleri açıklanmaktadır.

| Özellik | Ayrılmış veya iyi bilinen | Açıklama |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Ayrıldı | Şu anda kullanılmakta olan MSBuild ikililerinin bulunduğu klasörün mutlak yolu bulunur (örneğin, *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>). * Bu özellik, MSBuild dizinindeki dosyalara başvurmanız gerekiyorsa yararlıdır.<br /><br /> Bu özellik üzerinde son backslash eklemeyin. |
| `MSBuildExtensionsPath` | Tanın -mış | .NET Framework 4'te tanıtılan: varsayılan değerler `MSBuildExtensionsPath` ile `MSBuildExtensionsPath32`. Önceki sürümlerde varsayılan `MSBUILDLEGACYEXTENSIONSPATH` değer davranışını etkinleştirmek için ortam değişkenini `MSBuildExtensionsPath` null olmayan bir değere ayarlayabilirsiniz.<br /><br /> .NET Framework 3.5 ve önceki durumlarda, `MSBuildExtensionsPath` geçerli işlemin bitliğine bağlı *olarak,\Program\\ Dosyaları* veya *\Program Dosyaları (x86)* klasörünün altındaki MSBuild alt klasörünün yoluna işaret noktalarının varsayılan değeri. Örneğin, 64 bit makinedeki 32 bit işlem için bu özellik *\Program Dosyaları (x86)* klasörüne işaret eder. 64 bit makinedeki 64 bit işlem için bu özellik *\Program Dosyaları* klasörüne işaret ediyor.<br /><br /> Bu özellik üzerinde son backslash eklemeyin.<br /><br /> Bu konum, özel hedef dosyaları koymak için yararlı bir yerdir. Örneğin, hedef dosyalarınız *\Program Files\MSBuild\MyFiles\Northwind.targets* adresinde yüklenebilir ve bu XML kodunu kullanarak proje dosyalarına aktarılabilir:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Tanın -mış | *\Program Dosyaları* veya *\Program Dosyaları (x86)* klasörünün altındaki MSBuild alt klasörünün yolu. Yol her zaman 32 bit makinedeki 32 bit *\Program Dosyaları (x86)* klasörünü ve 64 bit makinedeki *\Program Dosyalarını* işaret eder." Ayrıca `MSBuildExtensionsPath` bakınız ve `MSBuildExtensionsPath64`.<br /><br /> Bu özellik üzerinde son backslash eklemeyin. |
| `MSBuildExtensionsPath64` | Tanın -mış | *\Program Dosyaları* klasörünün altındaki MSBuild alt klasörünün yolu. 64 bit lik bir makine için bu yol her zaman *\Program Dosyaları* klasörünü işaret edersiniz. 32 bitlik bir makine için bu yol boştur. Ayrıca `MSBuildExtensionsPath` bakınız ve `MSBuildExtensionsPath32`.<br /><br /> Bu özellik üzerinde son backslash eklemeyin. |
| `MSBuildInteractive` | Ayrıldı | `true`MSBuild etkileşimli olarak çalışıyorsa, kullanıcı girişine izin verir. Bu ayar `-interactive` komut satırı seçeneği tarafından denetlenir. |
| `MSBuildLastTaskResult` | Ayrıldı | `true`önceki görev herhangi bir hata olmadan tamamlanmışsa `false` (uyarılar olsa bile) veya önceki görevde hatalar varsa. Genellikle, bir görevde bir hata oluştuğunda, hata bu projede gerçekleşen son şeydir. Bu nedenle, bu özelliğin `false`değeri hiçbir zaman , bu senaryolar dışında:<br /><br /> `ContinueOnError` - [Görev öğesinin (MSBuild)](../msbuild/task-element-msbuild.md) özniteliği `WarnAndContinue` (veya `true`) `ErrorAndContinue`veya .<br /><br /> - Bir `Target` alt öğe olarak [onerror öğesi (MSBuild)](../msbuild/onerror-element-msbuild.md) olduğunda. |
| `MSBuildNodeCount` | Ayrıldı | Oluştururken kullanılan en fazla eşzamanlı işlem sayısı. Bu, komut satırında **-maxcpucount** için belirttiğiniz değerdir. Bir değer belirtmeden **-maxcpucount** belirtirseniz, bilgisayardaki `MSBuildNodeCount` işlemci sayısını belirtir. Daha fazla bilgi için komut [satırı başvurusuna](../msbuild/msbuild-command-line-reference.md) bakın ve [paralel olarak birden çok proje oluşturun.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) |
| `MSBuildProgramFiles32` | Ayrıldı | 32 bit program klasörünün konumu; örneğin, *C:\Program Dosyaları (x86)*.<br /><br /> Bu özellik üzerinde son backslash eklemeyin. |
| `MSBuildProjectDefaultTargets` | Ayrıldı | Öğenin özniteliği belirtilen `DefaultTargets` hedeflerin `Project` tam listesi. Örneğin, aşağıdaki `Project` öğenin `MSBuildDefaultTargets` `A;B;C`bir özellik değeri olurdu:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Ayrıldı | Proje dosyasının bulunduğu dizinin mutlak yolu, örneğin *C:\MyCompany\MyProduct*.<br /><br /> Bu özellik üzerinde son backslash eklemeyin. |
| `MSBuildProjectDirectoryNoRoot` | Ayrıldı | Kök sürücü `MSBuildProjectDirectory` hariç özelliğin değeri.<br /><br /> Bu özellik üzerinde son backslash eklemeyin. |
| `MSBuildProjectExtension` | Ayrıldı | Dönem de dahil olmak üzere proje dosyasının dosya adı uzantısı; örneğin, *.proj*. |
| `MSBuildProjectFile` | Ayrıldı | Dosya adı uzantısı da dahil olmak üzere proje dosyasının tam dosya adı; örneğin, *MyApp.proj*. |
| `MSBuildProjectFullPath` | Ayrıldı | Dosya adı uzantısı da dahil olmak üzere proje dosyasının mutlak yolu ve tam dosya adı; örneğin, *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Ayrıldı | Dosya adı uzantısı olmadan proje dosyasının dosya adı; örneğin, *MyApp*. |
| `MSBuildRuntimeType` | Ayrıldı | Şu anda yürütülmakta olan çalışma zamanının türü. MSBuild 15 ile tanıtıldı. Değer tanımlanmamış olabilir (MSBuild 15'ten `Full` önce), MSBuild'in masaüstünde `Core` çalıştığını belirten .NET Framework, MSBuild'in `dotnet build`.NET `Mono` Core'da çalıştığını (örneğin,) veya MSBuild'in Mono'da çalıştığını gösteren. |
| `MSBuildStartupDirectory` | Ayrıldı | MSBuild olarak adlandırılan klasörün mutlak yolu. Bu özelliği kullanarak, her dizinde * \<dirs>.proj* dosyaları oluşturmadan bir proje ağacında belirli bir noktanın altında her şeyi oluşturabilirsiniz. Bunun yerine, yalnızca bir projeniz var—örneğin, *c:\traversal.proj*, burada gösterildiği gibi:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Ağacın herhangi bir noktasında inşa etmek için şunları yazın:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Bu özellik üzerinde son backslash eklemeyin. |
| `MSBuildThisFile` | Ayrıldı | Dosya adı ve dosya `MSBuildThisFileFullPath`uzantısı bölümü. |
| `MSBuildThisFileDirectory` | Ayrıldı | Dizin `MSBuildThisFileFullPath`bölümü.<br /><br /> Son ters eğik çizgiyi yola ekleyin. |
| `MSBuildThisFileDirectoryNoRoot` | Ayrıldı | Kök sürücüsü hariç `MSBuildThisFileFullPath`dizin bölümü.<br /><br /> Son ters eğik çizgiyi yola ekleyin. |
| `MSBuildThisFileExtension` | Ayrıldı | Dosya adı uzantısı `MSBuildThisFileFullPath`bölümü. |
| `MSBuildThisFileFullPath` | Ayrıldı | Projenin veya çalışan hedefin içeren hedef dosyasının mutlak yolu.<br /><br /> İpucu: Hedef dosyasında, özgün proje dosyasıyla gören değil, hedef dosyasına göreli göreli bir yol belirtebilirsiniz. |
| `MSBuildThisFileName` | Ayrıldı | Dosya adı uzantısı `MSBuildThisFileFullPath`olmadan dosya adı bölümü. |
| `MSBuildToolsPath` | Ayrıldı | Değeri yle ilişkili MSBuild sürümünün `MSBuildToolsVersion`yükleme yolu<br /><br /> Son ters eğik çizgiyi yola eklemeyin.<br /><br /> Bu özellik geçersiz kılınamaz. |
| `MSBuildToolsVersion` | Ayrıldı | Projeyi oluşturmak için kullanılan MSBuild Araç Kümesi sürümü.<br /><br /> Not: MSBuild Araç Seti, bir uygulama oluşturmak için kullanılan görevlerden, hedeflerden ve araçlardan oluşur. Araçlar *csc.exe* ve *vbc.exe*gibi derleyiciler içerir. Daha fazla bilgi için [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)ve [Standart ve özel Araç Seti yapılandırmalarına](../msbuild/standard-and-custom-toolset-configurations.md)bakın. |
| `MSBuildVersion` | Ayrıldı | MSBuild sürümü proje oluşturmak için kullanılır. <br /><br/> Bu özellik geçersiz kılınamaz, aksi takdirde `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` hata iletisi döndürülür. |

## <a name="names-that-conflict-with-msbuild-elements"></a>MSBuild öğeleriyle çakışan adlar

Yukarıdakilere ek olarak, MSBuild dil öğelerine karşılık gelen adlar kullanıcı tanımlı özellikler, öğeler veya madde meta verileri için kullanılamaz:

* VisualStudioProjesi
* Hedef
* Propertygroup
* Çıktı
* ıtemgroup
* Usingtask
* Proje Uzantıları
* Onerror
* İthalat Grubu
* Seçin:
* Tesis
* Aksi takdir -de

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)

- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
