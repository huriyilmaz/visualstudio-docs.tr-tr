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
ms.openlocfilehash: 9f0288d0a8f8afb413ee6df4a2ca86fd79502900806aed5704185b7185c507d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121303416"
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
| `SourceModules` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir derlemeye Derlenecek bir veya daha fazla modül. Modüller, sonuçta elde edilen derlemenin bildiriminde listelenecektir ve derlemenin yüklenmesi için yine de dağıtılmalıdır ve kullanılabilir olacaktır. Bu parametreye geçirilen öğeler, `Target` dosyanın dosyayı kopyalayan yolu ve dosya adını belirten ek meta verilere sahip olabilir ve sonrasında bu yeni dosyayı derlemeye derler. Daha fazla bilgi için [Al.exe (derleme Bağlayıcısı)](/dotnet/framework/tools/al-exe-assembly-linker)belgelerine bakın. Bu parametre, belirli bir anahtar olmadan *Al.exe* geçirilen modül listesine karşılık gelir. |
| `TargetType` | İsteğe bağlı `String` parametre.<br /><br /> çıkış dosyasının dosya biçimini belirtir: `library` (kod kitaplığı), `exe` (konsol uygulaması) veya `win` (Windows tabanlı uygulama). Varsayılan değer: `library`. Bu parametre `/t[arget]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `TemplateFile` | İsteğe bağlı `String` parametre.<br /><br /> Kültür alanı dışında tüm derleme meta verilerinin devraldığı derlemeyi belirtir. Belirtilen derlemenin tanımlayıcı bir adı olmalıdır.<br /><br /> Parametresiyle oluşturduğunuz bir derleme, `TemplateFile` uydu bütünleştirilmiş kodu olacaktır. Bu parametre `/template` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `Timeout` | İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue` , zaman aşımı süresi olmadığını gösterir. |
| `Title` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `Title` . Daha fazla bilgi için `/title` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `ToolPath` | İsteğe bağlı `String` parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (Al.exe) yükleyecek konumu belirtir. Bu parametre belirtilmezse, görev, MSBuild çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `Trademark` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki alan için bir dize belirtir `Trademark` . Daha fazla bilgi için `/trade[mark]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Version` | İsteğe bağlı `String` parametre.<br /><br /> Bu derleme için sürüm bilgilerini belirtir. Dizenin biçimi *birincil. Minor. Build. Revision*. Varsayılan değer 0’dır. Daha fazla bilgi için `/v[ersion]` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Win32Icon` | İsteğe bağlı `String` parametre.<br /><br /> Derlemeye bir *. ico* dosyası ekler. *. İco* dosyası, çıktı dosyasına dosya Gezgini 'nde istenen görünümü verir. Bu parametre `/win32icon` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `Win32Resource` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına bir Win32 kaynağı (*. res* dosyası) ekler. Daha fazla bilgi için `/win32res` [Al.exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

 Aşağıdaki örnek, belirtilen seçeneklere sahip bir derleme oluşturur.

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
