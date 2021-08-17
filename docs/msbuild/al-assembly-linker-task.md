---
title: AL (derleme bağlayıcı) görevi | Microsoft Docs
description: Windows yazılım geliştirme seti ile dağıtılan bir araç olan AL.exe kaydırmak için MSBuild Assembly bağlayıcı (AL) görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: fa25fe5b06aa461b0628fff90a3a383228c9a5ca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055165"
---
# <a name="al-assembly-linker-task"></a>AL (Derleme Bağlayıcı) görevi

AL görevi, Windows yazılım geliştirme seti (SDK) ile dağıtılan bir araç olan *AL.exe* kaydırır. Bu derleme bağlayıcı aracı, modüller ya da kaynak dosyaları olan bir veya daha fazla dosyadan bildirim içeren bir derleme oluşturmak için kullanılır. Derleyiciler ve geliştirme ortamları bu özellikleri zaten sağlayabilir, bu yüzden genellikle bu görevi doğrudan kullanmak gerekli değildir. Derleme Bağlayıcı, karma dil geliştirmede üretilebilen gibi birden çok bileşen dosyasından tek bir derleme oluşturmalarına gerek duyan geliştiriciler için yararlıdır. Bu görev, modülleri tek bir derleme dosyasında birleştirmez; elde edilen derlemenin doğru bir şekilde yüklenmesi için bağımsız modüllerin hala dağıtılması ve kullanılabilir olması gerekir. *AL.exe* hakkında daha fazla bilgi için bkz. [Al.exe (derleme Bağlayıcısı)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `AL` .

| Parametre | Açıklama |
|---------------------| - |
| `AlgorithmID` | İsteğe bağlı `String` parametre.<br /><br /> Derleme bildirimini içeren dosya hariç, çok dosyalı bir derlemede tüm dosyaları karma yapmak için bir algoritma belirtir. Daha fazla bilgi için `/algid` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `BaseAddress` | İsteğe bağlı `String` parametre.<br /><br /> Çalışma zamanında kullanıcının bilgisayarına DLL yüklenecek adresi belirtir. İşletim sisteminin dll 'Leri işlem alanında yeniden konumlandırmalarına izin vermek yerine, dll 'lerin temel adresini belirtirseniz uygulamalar daha hızlı yüklenir. Bu parametre/Base[adresine](/dotnet/framework/tools/al-exe-assembly-linker)karşılık gelir. |
| `CompanyName` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `Company` . Daha fazla bilgi için `/comp[any]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Configuration` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `Configuration` . Daha fazla bilgi için `/config[uration]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Copyright` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `Copyright` . Daha fazla bilgi için `/copy[right]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Culture` | İsteğe bağlı `String` parametre.<br /><br /> Derleme ile ilişkilendirilecek için kültür dizeyini belirtir. Daha fazla bilgi için `/c[ulture]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true` derlemeye yalnızca ortak anahtar yerleştirmek için; `false` derlemeyi tamamen imzalamak için. Daha fazla bilgi için `/delay[sign]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Description` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `Description` . Daha fazla bilgi için `/descr[iption]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `EmbedResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Belirtilen kaynakları, derleme bildirimini içeren görüntüye gömer. Bu görev, kaynak dosyasının içeriğini görüntüye kopyalar. Bu parametreye geçirilen öğelere, ve olarak adlandırılan isteğe bağlı meta veriler eklenebilir `LogicalName` `Access` . `LogicalName`Meta veriler, kaynağın iç tanımlayıcısını belirtmek için kullanılır.  `Access`Meta veriler, `private` kaynağı diğer derlemelere görünür hale getirmek için olarak ayarlanabilir. Daha fazla bilgi için `/embed[resource]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `EvidenceFile` | İsteğe bağlı `String` parametre.<br /><br /> Belirtilen dosyayı, kaynak adı ile derlemeye gömer `Security.Evidence` .<br /><br /> `Security.Evidence`Normal kaynaklar için kullanamazsınız. Bu parametre `/e[vidence]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `ExitCode` | İsteğe bağlı `Int32` Çıkış salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından sunulan çıkış kodunu belirtir. |
| `FileVersion` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `File Version` . Daha fazla bilgi için `/fileversion` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Flags` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir değer belirtir `Flags` . Daha fazla bilgi için `/flags` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametre.<br /><br /> Görevin bir hata iletisinde bildirilen tüm dosyalar için mutlak yolu kullanmasına neden olur. Bu parametre `/fullpaths` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalar (ona tanımlayıcı ad verir). Görev daha sonra son derlemeyi özel anahtarla imzalayacaktır. Daha fazla bilgi için `/keyn[ame]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Bir derlemeyi imzalamak için bir anahtar çifti veya yalnızca ortak anahtar içeren bir dosyayı belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Daha fazla bilgi için `/keyf[ile]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Belirtilen kaynak dosyalarını bir derlemeye bağlar. Kaynak derlemenin bir parçası haline gelir, ancak dosya kopyalanmaz. Bu parametreye geçirilen öğelere,, ve olarak adlandırılan isteğe bağlı meta veriler eklenebilir `LogicalName` `Target` `Access` . `LogicalName`Meta veriler, kaynağın iç tanımlayıcısını belirtmek için kullanılır. `Target`Meta veriler, görevin dosyayı kopyalayabileceği yolu ve dosya adını belirtebilir ve sonrasında bu yeni dosyayı derlemeye derler. `Access`Meta veriler, `private` kaynağı diğer derlemelere görünür hale getirmek için olarak ayarlanabilir. Daha fazla bilgi için `/link[resource]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `MainEntryPoint` | İsteğe bağlı `String` parametre.<br /><br /> Bir modül yürütülebilir bir dosyaya dönüştürülürken giriş noktası olarak kullanılacak yöntemin tam adını (*Class. yöntemi*) belirtir. Bu parametre `/main` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `OutputAssembly` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan dosyanın adını belirtir. Bu parametre `/out` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Bu kodun çalıştırılabileceği platformu kısıtlar; ,, veya ' den biri olmalıdır `x86` `Itanium` `x64` `anycpu` . Varsayılan değer: `anycpu`. Bu parametre `/platform` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `ProductName` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `Product` . Daha fazla bilgi için `/prod[uct]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `ProductVersion` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `ProductVersion` . Daha fazla bilgi için `/productv[ersion]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `ResponseFiles` | İsteğe bağlı `String[]` parametre.<br /><br /> Derleme bağlayıcısına geçiş yapmak için ek seçenekler içeren yanıt dosyalarını belirtir. |
| `SdkToolsPath` | İsteğe bağlı `String` parametre.<br /><br /> resgen.exe gibi SDK araçlarının yolunu belirtir. |
| `SourceModules` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir derlemeye Derlenecek bir veya daha fazla modül. Modüller, sonuçta elde edilen derlemenin bildiriminde listelenecektir ve derlemenin yüklenmesi için yine de dağıtılmalıdır ve kullanılabilir olacaktır. Bu parametreye geçirilen öğeler, görevin dosyayı kopyalediği yolu ve dosya adını belirten adlı ek meta verilere sahip olabilir ve daha sonra bu yeni dosyayı derlemeye `Target` derler. Daha fazla bilgi içinAl.exe [(Assembly Linker) belgelerine bakın.](/dotnet/framework/tools/al-exe-assembly-linker) Bu parametre, belirli bir anahtar olmadanAl.exe *modül* listesine karşılık geldi. |
| `TargetType` | İsteğe `String` bağlı parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir: `library` (kod kitaplığı), `exe` (konsol uygulaması) veya `win` (Windows tabanlı uygulama). Varsayılan değer: `library`. Bu parametre,Al.exe `/t[arget]` [(Assembly Linker) içinde seçeneğine karşılık geldi.](/dotnet/framework/tools/al-exe-assembly-linker) |
| `TemplateFile` | İsteğe `String` bağlı parametre.<br /><br /> Kültür alanı dışında tüm derleme meta verileri devralınabilir derlemeyi belirtir. Belirtilen derlemenin bir güçlü adı olması gerekir.<br /><br /> parametresiyle birlikte bir `TemplateFile` derleme, bir uydu derlemesi olacak. Bu parametre,Al.exe `/template` [(Assembly Linker) içinde seçeneğine karşılık geldi.](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Timeout` | İsteğe `Int32` bağlı parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılma süresini milisaniye cinsinden belirtir. Varsayılan değer, `Int.MaxValue` zaman dışında nokta olmadığını gösteren değeridir. |
| `Title` | İsteğe `String` bağlı parametre.<br /><br /> Derlemede alanı için `Title` bir dize belirtir. Daha fazla bilgi içinAl.exe `/title` [(Assembly Linker) içinde seçeneğine ilişkin belgelere bakın.](/dotnet/framework/tools/al-exe-assembly-linker) |
| `ToolPath` | İsteğe `String` bağlı parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı yükley istediğiniz konumu belirtir (Al.exe). Bu parametre belirtilmezse, görev çalışan çerçevenin sürümüne karşılık gelen SDK yükleme yolunu MSBuild. |
| `Trademark` | İsteğe `String` bağlı parametre.<br /><br /> Derlemede alanı için `Trademark` bir dize belirtir. Daha fazla bilgi içinAl.exe `/trade[mark]` [(Assembly Linker) içinde seçeneğine ilişkin belgelere bakın.](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Version` | İsteğe `String` bağlı parametre.<br /><br /> Bu derleme için sürüm bilgilerini belirtir. Dizenin biçimi *major.minor.build.revision'tir.* Varsayılan değer 0’dır. Daha fazla bilgi içinAl.exe `/v[ersion]` [(Assembly Linker) içinde seçeneğine ilişkin belgelere bakın.](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Win32Icon` | İsteğe `String` bağlı parametre.<br /><br /> Derlemeye *bir .ico* dosyası ekler. *.ico dosyası,* çıkış dosyasına dosyanın istediğiniz görünümünü Dosya Gezgini. Bu parametre,Al.exe `/win32icon` [(Assembly Linker) içinde seçeneğine karşılık geldi.](/dotnet/framework/tools/al-exe-assembly-linker) |
| `Win32Resource` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış dosyasına bir Win32 kaynağı (*.res* dosyası) ekler. Daha fazla bilgi içinAl.exe `/win32res` [(Assembly Linker) içinde seçeneğine ilişkin belgelere bakın.](/dotnet/framework/tools/al-exe-assembly-linker) |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

 Aşağıdaki örnek, belirtilen seçeneklerle bir derleme oluşturur.

```xml
<AL
    EmbedResources="@(EmbeddedResource)"
    Culture="%(EmbeddedResource.Culture)"
    TemplateFile="@(IntermediateAssembly)"
    KeyContainer="$(KeyContainerName)"
    KeyFile="$(KeyOriginatorFile)"
    DelaySign="$(DelaySign)"

    OutputAssembly=
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">

    <Output TaskParameter="OutputAssembly"
        ItemName="SatelliteAssemblies"/>
</AL>
```

## <a name="see-also"></a>Ayrıca bkz.

* [Görev başvurusu](../msbuild/msbuild-task-reference.md)
* [Görevler](../msbuild/msbuild-tasks.md)
