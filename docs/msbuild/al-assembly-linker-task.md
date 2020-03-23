---
title: AL (Montaj Bağlayıcısı) Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 6861fee8691c32415111347ab673f9e48bfb9e11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634597"
---
# <a name="al-assembly-linker-task"></a>AL (Derleme Bağlayıcısı) görevi

AL görevi, Windows Yazılım Geliştirme Kiti (SDK) ile dağıtılan bir araç olan *AL.exe'yi*sarar. Bu Derleme Bağlayıcısı aracı, modül veya kaynak dosyaları olan bir veya daha fazla dosyadan bir bildirim içeren bir derleme oluşturmak için kullanılır. Derleyiciler ve geliştirme ortamları zaten bu yetenekleri sağlayabilir, bu nedenle genellikle bu görevi doğrudan kullanmak gerekli değildir. Derleme Bağlantı Cısı, karma dil geliştirmeden üretilebilenler gibi birden çok bileşen dosyasından tek bir derleme oluşturması gereken geliştiriciler için en yararlıdır. Bu görev, modülleri tek bir derleme dosyasında birleştirmez; ortaya çıkan montajın doğru yüklenmesi için modüllerin dağıtılmak ve kullanılabilmesi gerekir. *AL.exe*hakkında daha fazla bilgi için [al.exe (Derleme Bağlantı)](/dotnet/framework/tools/al-exe-assembly-linker)bakın.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `AL` açıklanmaktadır.

| Parametre | Açıklama |
|---------------------| - |
| `AlgorithmID` | İsteğe bağlı `String` parametre.<br /><br /> Derleme bildirimini içeren dosya hariç, çok dosyalı bir derlemede tüm dosyaları karma yapmak için bir algoritma belirtir. Daha fazla bilgi için `/algid` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `BaseAddress` | İsteğe bağlı `String` parametre.<br /><br /> Çalışma zamanında kullanıcının bilgisayarına DLL yüklenecek adresi belirtir. İşletim sisteminin Işlem alanıiçinde DL'lerin yerini değiştirmesine izin vermek yerine, DL'lerin temel adresini belirtirseniz uygulamalar daha hızlı yüklenir. Bu parametre /temel[adrese](/dotnet/framework/tools/al-exe-assembly-linker)karşılık gelir. |
| `CompanyName` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Company` alan için bir dize belirtir. Daha fazla bilgi için `/comp[any]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `Configuration` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Configuration` alan için bir dize belirtir. Daha fazla bilgi için `/config[uration]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `Copyright` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Copyright` alan için bir dize belirtir. Daha fazla bilgi için `/copy[right]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `Culture` | İsteğe bağlı `String` parametre.<br /><br /> Derleme ile ilişkilendirilecek için kültür dizeyini belirtir. Daha fazla bilgi için `/c[ulture]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`sadece ortak anahtarı meclise yerleştirmek için; `false` tam olarak montaj imzalamak için. Daha fazla bilgi için `/delay[sign]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `Description` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Description` alan için bir dize belirtir. Daha fazla bilgi için `/descr[iption]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `EmbedResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Belirtilen kaynakları derleme bildirimini içeren görüntüye katıştırıyor. Bu görev, kaynak dosyasının içeriğini görüntüye kopyalar. Bu parametreye geçirilen öğeler, bunlara bağlı olarak `LogicalName` adlandırılan `Access`ve . Meta `LogicalName` veriler, kaynağın iç tanımlayıcısını belirtmek için kullanılır.  Meta `Access` veriler, kaynağın `private` diğer derlemeler tarafından görünür olmaması için ayarlanabilir. Daha fazla bilgi için `/embed[resource]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `EvidenceFile` | İsteğe bağlı `String` parametre.<br /><br /> Belirtilen dosyayı derlemeye kaynak adı ile `Security.Evidence`birlikte katıştırıyor.<br /><br /> Normal kaynaklar `Security.Evidence` için kullanamazsınız. Bu parametre `/e[vidence]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `ExitCode` | İsteğe bağlı `Int32` çıktı salt okunur parametresi.<br /><br /> Çalıştırılan komut tarafından sağlanan çıkış kodunu belirtir. |
| `FileVersion` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `File Version` alan için bir dize belirtir. Daha fazla bilgi için `/fileversion` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `Flags` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Flags` alan için bir değer belirtir. Daha fazla bilgi için `/flags` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametre.<br /><br /> Görevin hata iletisinde bildirilen dosyalar için mutlak yolu kullanmasına neden olur. Bu parametre `/fullpaths` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Anahtar çifti içeren bir kapsayıcıyı belirtir. Bu, derleme bildirimine ortak anahtar ekleyerek derlemeyi imzalar (ona tanımlayıcı ad verir). Görev daha sonra özel anahtarla son derlemeyi imzalar. Daha fazla bilgi için `/keyn[ame]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Bir derlemeyi imzalamak için anahtar çifti veya yalnızca ortak anahtar içeren bir dosya belirtir. Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Daha fazla bilgi için `/keyf[ile]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Belirtilen kaynak dosyalarını bir derlemeye bağlar. Kaynak derlemenin bir parçası olur, ancak dosya kopyalanmaz. Bu parametreye geçirilen öğeler, bunlara bağlı olarak `LogicalName`ekli `Target`" `Access`ve . Meta `LogicalName` veriler, kaynağın iç tanımlayıcısını belirtmek için kullanılır. Meta `Target` veriler, görevin dosyayı kopyaladığı yolu ve dosya adını belirtebilir ve bu yeni dosyayı derlemeye derleyebilir. Meta `Access` veriler, kaynağın `private` diğer derlemeler tarafından görünür olmaması için ayarlanabilir. Daha fazla bilgi için `/link[resource]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `MainEntryPoint` | İsteğe bağlı `String` parametre.<br /><br /> Bir modülü çalıştırılabilir bir dosyaya dönüştürürken giriş noktası olarak kullanılacak yöntemin tam nitelikli adını *(class.method)* belirtir. Bu parametre `/main` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `OutputAssembly` | Gerekli <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan dosyanın adını belirtir. Bu parametre `/out` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Bu kodun hangi platformda çalıştırılabildiği sınırlar; , `x86`, `Itanium` `x64`veya `anycpu`. Varsayılan değer: `anycpu`. Bu parametre `/platform` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `ProductName` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Product` alan için bir dize belirtir. Daha fazla bilgi için `/prod[uct]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `ProductVersion` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `ProductVersion` alan için bir dize belirtir. Daha fazla bilgi için `/productv[ersion]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `ResponseFiles` | İsteğe bağlı `String[]` parametre.<br /><br /> Derleme Bağlayıcısı'na geçmek için ek seçenekler içeren yanıt dosyalarını belirtir. |
| `SdkToolsPath` | İsteğe bağlı `String` parametre.<br /><br /> Resgen.exe gibi SDK araçlarına giden yolu belirtir. |
| `SourceModules` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir veya daha fazla modül bir derleme içine derlenecek. Modüller, ortaya çıkan derlemenin bildiriminde listelenecektir ve montajın yüklenmesi için dağıtılmak ve kullanılabilir olması gerekir. Bu parametreye geçirilen `Target`öğeler, görevin dosyayı kopyaladığı yolu ve dosya adını belirten ve bu yeni dosyayı derlemeye sonra derleyen ek meta verilere sahip olabilir. Daha fazla bilgi için [Al.exe (Derleme Bağlantı Cıstı) belgelerine](/dotnet/framework/tools/al-exe-assembly-linker)bakın. Bu parametre, belirli bir anahtar olmadan *Al.exe'ye* aktarılan modüller listesine karşılık gelir. |
| `TargetType` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir: `library` (kod `exe` kitaplığı), (konsol uygulaması) veya `win` (Windows tabanlı uygulama). Varsayılan değer: `library`. Bu parametre `/t[arget]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `TemplateFile` | İsteğe bağlı `String` parametre.<br /><br /> Kültür alanı dışında tüm derleme meta verilerini devralmak için derlemeyi belirtir. Belirtilen derlemenin güçlü bir adı olmalıdır.<br /><br /> `TemplateFile` Parametre ile oluşturduğunuz bir derleme bir uydu derlemesi olacaktır. Bu parametre `/template` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `Timeout` | İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir sonlandırıldıktan sonra milisaniye cinsinden süreyi belirtir. Varsayılan `Int.MaxValue`değer, zaman dışında bir dönem olmadığını gösterir. |
| `Title` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Title` alan için bir dize belirtir. Daha fazla bilgi için `/title` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `ToolPath` | İsteğe bağlı `String` parametre.<br /><br /> Görevin temel yürütülebilir dosyayı (Al.exe) yükleyeceği konumu belirtir. Bu parametre belirtilmemişse, görev MSBuild çalıştıran çerçevenin sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `Trademark` | İsteğe bağlı `String` parametre.<br /><br /> Derlemedeki `Trademark` alan için bir dize belirtir. Daha fazla bilgi için `/trade[mark]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `Version` | İsteğe bağlı `String` parametre.<br /><br /> Bu derlemenin sürüm bilgilerini belirtir. Dize biçimi *major.minor.build.revision*. Varsayılan değer 0’dır. Daha fazla bilgi için `/v[ersion]` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |
| `Win32Icon` | İsteğe bağlı `String` parametre.<br /><br /> Derlemeye *bir .ico* dosyası ekler. *.ico* dosyası çıktı dosyasına Dosya Gezgini'nde istenilen görünümü verir. Bu parametre `/win32icon` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğine karşılık gelir. |
| `Win32Resource` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına win32 kaynağı *(.res* dosyası) ekler. Daha fazla bilgi için `/win32res` [Al.exe (Derleme Bağlantı Cısrı)](/dotnet/framework/tools/al-exe-assembly-linker)seçeneğiiçin belgelere bakın. |

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [ToolTaskExtension taban sınıfına](../msbuild/tooltaskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, belirtilen seçenekleri içeren bir derleme oluşturur.

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
