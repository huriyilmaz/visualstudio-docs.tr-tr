---
title: AL (derleme bağlayıcı) görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c7964c6654d1f6996d1acc44542e3a7bf093a52
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167468"
---
# <a name="al-assembly-linker-task"></a>AL (derleme bağlayıcı) görevi

AL görevi, Windows yazılım geliştirme seti (SDK) ile dağıtılan bir araç olan *al. exe*' yi sarmalanmış. Bu derleme bağlayıcı aracı, modüller ya da kaynak dosyaları olan bir veya daha fazla dosyadan bildirim içeren bir derleme oluşturmak için kullanılır. Derleyiciler ve geliştirme ortamları bu özellikleri zaten sağlayabilir, bu yüzden genellikle bu görevi doğrudan kullanmak gerekli değildir. Derleme Bağlayıcı, karma dil geliştirmede üretilebilen gibi birden çok bileşen dosyasından tek bir derleme oluşturmalarına gerek duyan geliştiriciler için yararlıdır. Bu görev, modülleri tek bir derleme dosyasında birleştirmez; elde edilen derlemenin doğru bir şekilde yüklenmesi için bağımsız modüllerin hala dağıtılması ve kullanılabilir olması gerekir. *Al. exe*hakkında daha fazla bilgi için bkz. [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, `AL` görevin parametrelerini açıklar.

| Parametre | Açıklama |
|---------------------| - |
| `AlgorithmID` | İsteğe `String` bağlı parametre.<br /><br /> Derleme bildirimini içeren dosya hariç, çok dosyalı bir derlemede tüm dosyaları karma yapmak için bir algoritma belirtir. Daha fazla bilgi için `/algid` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `BaseAddress` | İsteğe `String` bağlı parametre.<br /><br /> Çalışma zamanında kullanıcının bilgisayarına DLL yüklenecek adresi belirtir. İşletim sisteminin dll 'Leri işlem alanında yeniden konumlandırmalarına izin vermek yerine, dll 'lerin temel adresini belirtirseniz uygulamalar daha hızlı yüklenir. Bu parametre/Base[adresine](/dotnet/framework/tools/al-exe-assembly-linker)karşılık gelir. |
| `CompanyName` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Company` alan için bir dize belirtir. Daha fazla bilgi için `/comp[any]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Configuration` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Configuration` alan için bir dize belirtir. Daha fazla bilgi için `/config[uration]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Copyright` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Copyright` alan için bir dize belirtir. Daha fazla bilgi için `/copy[right]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Culture` | İsteğe `String` bağlı parametre.<br /><br /> Derleme ile ilişkilendirilecek için kültür dizeyini belirtir. Daha fazla bilgi için `/c[ulture]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `DelaySign` | İsteğe `Boolean` bağlı parametre.<br /><br /> `true`derlemeye yalnızca ortak anahtar yerleştirmek için; `false` derlemeyi tamamen imzalamak için. Daha fazla bilgi için `/delay[sign]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Description` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Description` alan için bir dize belirtir. Daha fazla bilgi için `/descr[iption]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `EmbedResources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Belirtilen kaynakları, derleme bildirimini içeren görüntüye gömer. Bu görev, kaynak dosyasının içeriğini görüntüye kopyalar. Bu parametreye geçirilen öğelere, ve `LogicalName` `Access`olarak adlandırılan isteğe bağlı meta veriler eklenebilir. `LogicalName` Meta veriler, kaynağın iç tanımlayıcısını belirtmek için kullanılır.  Meta `Access` veriler, kaynağı diğer derlemelere `private` görünür hale getirmek için olarak ayarlanabilir. Daha fazla bilgi için `/embed[resource]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `EvidenceFile` | İsteğe `String` bağlı parametre.<br /><br /> Belirtilen dosyayı, kaynak adı ile derlemeye gömer `Security.Evidence`.<br /><br /> Normal kaynaklar için `Security.Evidence` kullanamazsınız. Bu parametre `/e[vidence]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `ExitCode` | İsteğe `Int32` bağlı çıkış salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından sunulan çıkış kodunu belirtir. |
| `FileVersion` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `File Version` alan için bir dize belirtir. Daha fazla bilgi için `/fileversion` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Flags` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Flags` alan için bir değer belirtir. Daha fazla bilgi için `/flags` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `GenerateFullPaths` | İsteğe `Boolean` bağlı parametre.<br /><br /> Görevin bir hata iletisinde bildirilen tüm dosyalar için mutlak yolu kullanmasına neden olur. Bu parametre `/fullpaths` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `KeyContainer` | İsteğe `String` bağlı parametre.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalar (ona tanımlayıcı ad verir). Görev daha sonra son derlemeyi özel anahtarla imzalayacaktır. Daha fazla bilgi için `/keyn[ame]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `KeyFile` | İsteğe `String` bağlı parametre.<br /><br /> Bir derlemeyi imzalamak için bir anahtar çifti veya yalnızca ortak anahtar içeren bir dosyayı belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Daha fazla bilgi için `/keyf[ile]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `LinkResources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Belirtilen kaynak dosyalarını bir derlemeye bağlar. Kaynak derlemenin bir parçası haline gelir, ancak dosya kopyalanmaz. Bu parametreye geçirilen öğelere, `LogicalName` `Target`, ve `Access`olarak adlandırılan isteğe bağlı meta veriler eklenebilir. `LogicalName` Meta veriler, kaynağın iç tanımlayıcısını belirtmek için kullanılır. `Target` Meta veriler, görevin dosyayı kopyalayabileceği yolu ve dosya adını belirtebilir ve sonrasında bu yeni dosyayı derlemeye derler. Meta `Access` veriler, kaynağı diğer derlemelere `private` görünür hale getirmek için olarak ayarlanabilir. Daha fazla bilgi için `/link[resource]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `MainEntryPoint` | İsteğe `String` bağlı parametre.<br /><br /> Bir modül yürütülebilir bir dosyaya dönüştürülürken giriş noktası olarak kullanılacak yöntemin tam adını (*Class. yöntemi*) belirtir. Bu parametre `/main` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `OutputAssembly` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan dosyanın adını belirtir. Bu parametre `/out` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `Platform` | İsteğe `String` bağlı parametre.<br /><br /> Bu kodun çalıştırılabileceği platformu kısıtlar; `x86` `Itanium`, `x64`, veya `anycpu`' den biri olmalıdır. Varsayılan değer: `anycpu`. Bu parametre `/platform` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `ProductName` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Product` alan için bir dize belirtir. Daha fazla bilgi için `/prod[uct]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `ProductVersion` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `ProductVersion` alan için bir dize belirtir. Daha fazla bilgi için `/productv[ersion]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `ResponseFiles` | İsteğe `String[]` bağlı parametre.<br /><br /> Derleme bağlayıcısına geçiş yapmak için ek seçenekler içeren yanıt dosyalarını belirtir. |
| `SdkToolsPath` | İsteğe `String` bağlı parametre.<br /><br /> Resgen. exe gibi SDK araçlarının yolunu belirtir. |
| `SourceModules` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bir derlemeye Derlenecek bir veya daha fazla modül. Modüller, sonuçta elde edilen derlemenin bildiriminde listelenecektir ve derlemenin yüklenmesi için yine de dağıtılmalıdır ve kullanılabilir olacaktır. Bu parametreye geçirilen öğeler, dosyanın dosyayı kopyalayan yolu ve dosya `Target`adını belirten ek meta verilere sahip olabilir ve sonrasında bu yeni dosyayı derlemeye derler. Daha fazla bilgi için bkz. [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)belgeleri. Bu parametre, belirli bir anahtar olmadan *al. exe* ' ye geçirilen modüllerin listesine karşılık gelir. |
| `TargetType` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış dosyasının dosya biçimini belirtir: `library` (kod kitaplığı), `exe` (konsol uygulaması) veya `win` (Windows tabanlı uygulama). Varsayılan değer: `library`. Bu parametre `/t[arget]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `TemplateFile` | İsteğe `String` bağlı parametre.<br /><br /> Kültür alanı dışında tüm derleme meta verilerinin devraldığı derlemeyi belirtir. Belirtilen derlemenin tanımlayıcı bir adı olmalıdır.<br /><br /> Parametresiyle oluşturduğunuz bir derleme, `TemplateFile` uydu bütünleştirilmiş kodu olacaktır. Bu parametre `/template` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `Timeout` | İsteğe `Int32` bağlı parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue`, zaman aşımı süresi olmadığını gösterir. |
| `Title` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Title` alan için bir dize belirtir. Daha fazla bilgi için `/title` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `ToolPath` | İsteğe `String` bağlı parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (al. exe) yükleneceği konumu belirtir. Bu parametre belirtilmezse, görev MSBuild çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `Trademark` | İsteğe `String` bağlı parametre.<br /><br /> Derlemedeki `Trademark` alan için bir dize belirtir. Daha fazla bilgi için `/trade[mark]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Version` | İsteğe `String` bağlı parametre.<br /><br /> Bu derleme için sürüm bilgilerini belirtir. Dizenin biçimi *birincil. Minor. Build. Revision*. Varsayılan değer 0’dır. Daha fazla bilgi için `/v[ersion]` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |
| `Win32Icon` | İsteğe `String` bağlı parametre.<br /><br /> Derlemeye bir *. ico* dosyası ekler. *. İco* dosyası, çıktı dosyasına dosya Gezgini 'nde istenen görünümü verir. Bu parametre `/win32icon` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe karşılık gelir. |
| `Win32Resource` | İsteğe `String` bağlı parametre.<br /><br /> Çıktı dosyasına bir Win32 kaynağı (*. res* dosyası) ekler. Daha fazla bilgi için `/win32res` [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)' daki seçeneğe yönelik belgelere bakın. |

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
