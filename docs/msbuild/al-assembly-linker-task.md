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
ms.openlocfilehash: d90e6c94d07b73e79d793982944bca395a562df2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593479"
---
# <a name="al-assembly-linker-task"></a>AL (derleme bağlayıcı) görevi
AL görevi, [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]dağıtılan bir araç olan *al. exe*' yi kaydırır. Bu derleme bağlayıcı aracı, modüller ya da kaynak dosyaları olan bir veya daha fazla dosyadan bildirim içeren bir derleme oluşturmak için kullanılır. Derleyiciler ve geliştirme ortamları bu özellikleri zaten sağlayabilir, bu yüzden genellikle bu görevi doğrudan kullanmak gerekli değildir. Derleme Bağlayıcı, karma dil geliştirmede üretilebilen gibi birden çok bileşen dosyasından tek bir derleme oluşturmalarına gerek duyan geliştiriciler için yararlıdır. Bu görev, modülleri tek bir derleme dosyasında birleştirmez; elde edilen derlemenin doğru bir şekilde yüklenmesi için bağımsız modüllerin hala dağıtılması ve kullanılabilir olması gerekir. *Al. exe*hakkında daha fazla bilgi için bkz. [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `AL` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|---------------------| - |
| `AlgorithmID` | İsteğe bağlı `String` parametresi.<br /><br /> Derleme bildirimini içeren dosya hariç, çok dosyalı bir derlemede tüm dosyaları karma yapmak için bir algoritma belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/algid` seçeneği için belgelere bakın. |
| `BaseAddress` | İsteğe bağlı `String` parametresi.<br /><br /> Çalışma zamanında kullanıcının bilgisayarına DLL yüklenecek adresi belirtir. İşletim sisteminin dll 'Leri işlem alanında yeniden konumlandırmalarına izin vermek yerine, dll 'lerin temel adresini belirtirseniz uygulamalar daha hızlı yüklenir. Bu parametre/Base[adresine](/dotnet/framework/tools/al-exe-assembly-linker)karşılık gelir. |
| `CompanyName` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Company` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/comp[any]` seçeneği için belgelere bakın. |
| `Configuration` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Configuration` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/config[uration]` seçeneği için belgelere bakın. |
| `Copyright` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Copyright` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/copy[right]` seçeneği için belgelere bakın. |
| `Culture` | İsteğe bağlı `String` parametresi.<br /><br /> Derleme ile ilişkilendirilecek için kültür dizeyini belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/c[ulture]` seçeneği için belgelere bakın. |
| `DelaySign` | İsteğe bağlı `Boolean` parametresi.<br /><br /> derlemeye yalnızca ortak anahtar yerleştirmek için `true`; derlemeyi tam olarak imzalamak için `false`. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/delay[sign]` seçeneği için belgelere bakın. |
| `Description` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Description` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/descr[iption]` seçeneği için belgelere bakın. |
| `EmbedResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Belirtilen kaynakları, derleme bildirimini içeren görüntüye gömer. Bu görev, kaynak dosyasının içeriğini görüntüye kopyalar. Bu parametreye geçirilen öğelere, `LogicalName` ve `Access`olarak adlandırılan isteğe bağlı meta veriler eklenebilir. `LogicalName` meta verileri, kaynağın iç tanımlayıcısını belirtmek için kullanılır.  `Access` meta verileri, kaynağı diğer derlemelere görünmez hale getirmek için `private` olarak ayarlanabilir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/embed[resource]` seçeneği için belgelere bakın. |
| `EvidenceFile` | İsteğe bağlı `String` parametresi.<br /><br /> `Security.Evidence`kaynak adı ile, belirtilen dosyayı derlemeye gömer.<br /><br /> Normal kaynaklar için `Security.Evidence` kullanamazsınız. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/e[vidence]` seçeneğe karşılık gelir. |
| `ExitCode` | İsteğe bağlı `Int32` çıkışı salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından sunulan çıkış kodunu belirtir. |
| `FileVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `File Version` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/fileversion` seçeneği için belgelere bakın. |
| `Flags` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Flags` alanı için bir değer belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/flags` seçeneği için belgelere bakın. |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Görevin bir hata iletisinde bildirilen tüm dosyalar için mutlak yolu kullanmasına neden olur. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/fullpaths` seçeneğe karşılık gelir. |
| `KeyContainer` | İsteğe bağlı `String` parametresi.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalar (ona tanımlayıcı ad verir). Görev daha sonra son derlemeyi özel anahtarla imzalayacaktır. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/keyn[ame]` seçeneği için belgelere bakın. |
| `KeyFile` | İsteğe bağlı `String` parametresi.<br /><br /> Bir derlemeyi imzalamak için bir anahtar çifti veya yalnızca ortak anahtar içeren bir dosyayı belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/keyf[ile]` seçeneği için belgelere bakın. |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Belirtilen kaynak dosyalarını bir derlemeye bağlar. Kaynak derlemenin bir parçası haline gelir, ancak dosya kopyalanmaz. Bu parametreye geçirilen öğelere, `LogicalName`, `Target`ve `Access`olarak adlandırılan isteğe bağlı meta veriler eklenebilir. `LogicalName` meta verileri, kaynağın iç tanımlayıcısını belirtmek için kullanılır. `Target` meta verileri, görevin dosyayı kopyalayabileceği yolu ve dosya adını belirtebilir ve sonrasında bu yeni dosyayı derlemeye derler. `Access` meta verileri, kaynağı diğer derlemelere görünmez hale getirmek için `private` olarak ayarlanabilir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/link[resource]` seçeneği için belgelere bakın. |
| `MainEntryPoint` | İsteğe bağlı `String` parametresi.<br /><br /> Bir modül yürütülebilir bir dosyaya dönüştürülürken giriş noktası olarak kullanılacak yöntemin tam adını (*Class. yöntemi*) belirtir. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/main` seçeneğe karşılık gelir. |
| `OutputAssembly` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıktı parametresi.<br /><br /> Bu görev tarafından oluşturulan dosyanın adını belirtir. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/out` seçeneğe karşılık gelir. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Bu kodun çalıştırılabileceği platformu kısıtlar; `x86`, `Itanium`, `x64`veya `anycpu`biri olmalıdır. Varsayılan, `anycpu` değeridir. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/platform` seçeneğe karşılık gelir. |
| `ProductName` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Product` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/prod[uct]` seçeneği için belgelere bakın. |
| `ProductVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `ProductVersion` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/productv[ersion]` seçeneği için belgelere bakın. |
| `ResponseFiles` | İsteğe bağlı `String[]` parametresi.<br /><br /> Derleme bağlayıcısına geçiş yapmak için ek seçenekler içeren yanıt dosyalarını belirtir. |
| `SdkToolsPath` | İsteğe bağlı `String` parametresi.<br /><br /> Resgen. exe gibi SDK araçlarının yolunu belirtir. |
| `SourceModules` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir derlemeye Derlenecek bir veya daha fazla modül. Modüller, sonuçta elde edilen derlemenin bildiriminde listelenecektir ve derlemenin yüklenmesi için yine de dağıtılmalıdır ve kullanılabilir olacaktır. Bu parametreye geçirilen öğelerin, dosyayı kopyalayan yolu ve dosya adını belirten `Target`adlı ek meta veriler olabilir ve sonrasında bu yeni dosyayı derlemeye derler. Daha fazla bilgi için bkz. [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)belgeleri. Bu parametre, belirli bir anahtar olmadan *al. exe* ' ye geçirilen modüllerin listesine karşılık gelir. |
| `TargetType` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyasının dosya biçimini belirtir: `library` (kod kitaplığı), `exe` (konsol uygulaması) veya `win` (Windows tabanlı uygulama). Varsayılan, `library` değeridir. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/t[arget]` seçeneğe karşılık gelir. |
| `TemplateFile` | İsteğe bağlı `String` parametresi.<br /><br /> Kültür alanı dışında tüm derleme meta verilerinin devraldığı derlemeyi belirtir. Belirtilen derlemenin tanımlayıcı bir adı olmalıdır.<br /><br /> `TemplateFile` parametresiyle oluşturduğunuz bir derleme uydu bütünleştirilmiş kodu olacaktır. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/template` seçeneğe karşılık gelir. |
| `Timeout` | İsteğe bağlı `Int32` parametresi.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer, zaman aşımı süresi olmadığını belirten `Int.MaxValue`. |
| `Title` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Title` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/title` seçeneği için belgelere bakın. |
| `ToolPath` | İsteğe bağlı `String` parametresi.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (al. exe) yükleneceği konumu belirtir. Bu parametre belirtilmezse, görev, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `Trademark` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemedeki `Trademark` alanı için bir dize belirtir. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/trade[mark]` seçeneği için belgelere bakın. |
| `Version` | İsteğe bağlı `String` parametresi.<br /><br /> Bu derleme için sürüm bilgilerini belirtir. Dizenin biçimi *birincil. Minor. Build. Revision*. Varsayılan değer 0'dır. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/v[ersion]` seçeneği için belgelere bakın. |
| `Win32Icon` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemeye bir *. ico* dosyası ekler. *. İco* dosyası, çıktı dosyasına dosya Gezgini 'nde istenen görünümü verir. Bu parametre [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/win32icon` seçeneğe karşılık gelir. |
| `Win32Resource` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyasına bir Win32 kaynağı ( *. res* dosyası) ekler. Daha fazla bilgi için [al. exe (bütünleştirilmiş kod bağlayıcı)](/dotnet/framework/tools/al-exe-assembly-linker)içindeki `/win32res` seçeneği için belgelere bakın. |

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.ToolTask> sınıfından devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).

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
