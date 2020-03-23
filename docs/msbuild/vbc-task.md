---
title: Vbc Görevi | Microsoft Dokümanlar
ms.date: 04/12/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1710336ebc73be707e962733e37376b5689e10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631243"
---
# <a name="vbc-task"></a>Vbc görevi

Yürütülebilir (*.exe*), dinamik bağlantı kitaplıkları (*.dll*) veya kod modülleri (*.netmodule)* üreten *vbc.exe'yi*sarar. *vbc.exe*hakkında daha fazla bilgi için [Visual Basic komut satırı derleyicisi'ne](/dotnet/visual-basic/reference/command-line-compiler/index)bakın.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `Vbc` açıklanmaktadır.

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametre.<br /><br /> Başvurular özniteliği'nde belirtilen derlemeleri aramak için ek klasörler belirtir. |
| `AddModules` | İsteğe bağlı `String[]` parametre.<br /><br /> Derleyicinin, şu anda derlemekte olduğunuz projeiçin belirtilen dosya(lar)daki tüm tür bilgilerini kullanılabilir hale getirmelerine neden olur. Bu parametre *vbc.exe* derleyicisinin [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) anahtarına karşılık gelir. |
| `BaseAddress` | İsteğe bağlı `String` parametre.<br /><br /> DLL'nin temel adresini belirtir. Bu parametre *vbc.exe* derleyicisinin [-baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) anahtarına karşılık gelir. |
| `CodePage` | İsteğe bağlı `Int32` parametre.<br /><br /> Derlemedeki tüm kaynak kod dosyaları için kullanılacak kod sayfasını belirtir. Bu parametre *vbc.exe* derleyicisinin [-codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) anahtarına karşılık gelir. |
| `DebugType` | İsteğe bağlı `String[]` parametre.<br /><br /> Derleyicinin hata ayıklama bilgileri oluşturmasına neden olur. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Varsayılan değer, `full`çalışan programa hata ayıklama eklemeyi sağlayan değerdir. Program hata `pdbonly` ayıklayıcıda başlatıldığında kaynak kodunun hata ayıklanmasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde derleme dil kodunu görüntüler. Daha fazla bilgi için bkz: [-hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | İsteğe bağlı `String[]` parametre.<br /><br /> Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri yarı kolonlarla ayrılır ve aşağıdaki sözdizimi ile belirtilir:<br /><br /> *sembol1* `=` *değer1* `;` *sembol2* `=` *değer2*<br /><br /> Bu parametre *vbc.exe* derleyicisinin [-define](/dotnet/visual-basic/reference/command-line-compiler/define) anahtarına karşılık gelir. |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`görev ortak anahtarı derlemeye yerleştirir. Eğer `false`, görev tam olarak montaj imzalar. Varsayılan `false`değer. `KeyFile` Parametre veya `KeyContainer` parametre ile kullanılmadığı sürece bu parametrenin hiçbir etkisi yoktur. Bu parametre *vbc.exe* derleyicisinin [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) anahtarına karşılık gelir. |
| `Deterministic` | İsteğe bağlı `Boolean` parametre.<br/><br/> Eğer, `true`derleyicinin, girişler aynıysa, ikili içeriği derlemeler arasında aynı olan bir derlemeyi çıktısına neden olur.<br/><br/>Daha fazla bilgi için bkz: [-deterministic](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | İsteğe bağlı `String` parametre.<br /><br /> Belirtilen uyarıları bastırır. Yalnızca uyarı tanımlayıcısının sayısal kısmını belirtmeniz gerekir. Birden çok uyarı yarım kolon ile ayrılır. Bu parametre *vbc.exe* derleyicisinin [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) anahtarına karşılık gelir. |
| `DocumentationFile` | İsteğe bağlı `String` parametre.<br /><br /> Belge açıklamalarını belirtilen XML dosyasına işler. Bu parametre özniteliği geçersiz kılar. `GenerateDocumentation` Daha fazla bilgi için bkz: [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, görev hata ayıklama bilgileri oluşturur ve bir *.pdb* dosyasına yerleştirir. Daha fazla bilgi için bkz: [-hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | İsteğe bağlı `String` parametre.<br /><br /> Görevin iç derleyici hatalarını nasıl bildirmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> `prompt` Belirtilirse ve bir iç derleyici hatası oluşursa, kullanıcıdan hata verilerini Microsoft'a gönderip göndermeme seçeneği istenir.<br /><br /> `send` Belirtilirse ve bir iç derleyici hatası oluşursa, görev hata verilerini Microsoft'a gönderir.<br /><br /> Varsayılan değer, `none`yalnızca metin çıkışındaki hataları bildiren değerdir.<br /><br /> Bu parametre *vbc.exe* derleyicisinin [-hata raporu](/dotnet/visual-basic/reference/command-line-compiler/errorreport) anahtarına karşılık gelir. |
| `FileAlignment` | İsteğe bağlı `Int32` parametre.<br /><br /> Çıktı dosyasının bölümlerini hizalamanın baytlar halinde olduğunu belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Bu parametre *vbc.exe* derleyicisinin [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) anahtarına karşılık gelir. |
| `GenerateDocumentation` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Belge bilgilerini oluşturur ve görevin oluşturduğu yürütülebilir dosya veya kitaplığın adını içeren bir XML dosyasına yerleştirir. Daha fazla bilgi için bkz: [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Belirtilen madde koleksiyonlarından ad alanlarını alır. Bu parametre *vbc.exe* derleyicisinin [-içe alma](/dotnet/visual-basic/reference/command-line-compiler/imports) anahtarına karşılık gelir. |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtar kapsayıcısının adını belirtir. Bu parametre *vbc.exe* derleyicisinin [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) anahtarına karşılık gelir. |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz: [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> "15.5" gibi [dil sürümünü](/dotnet/visual-basic/language-reference/configure-language-version)belirtir. |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıktı dosyasındaki bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıktı dosyasına yerleştirilmez. Bu parametre *vbc.exe* derleyicisinin [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) anahtarına karşılık gelir. |
| `MainEntryPoint` | İsteğe bağlı `String` parametre.<br /><br /> `Sub Main` Yordamı içeren sınıfı veya modülü belirtir. Bu parametre *vbc.exe* derleyicisinin [-ana](/dotnet/visual-basic/reference/command-line-compiler/main) anahtarına karşılık gelir. |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Bu modülün bir parçası olduğunu derleme belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyicinin *vbc.rsp* dosyasını kullanmaması gerektiğini belirtir. Bu parametre *vbc.exe* derleyicisinin [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametresine karşılık gelir. |
| `NoLogo` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`derleyici banner bilgilerinin görüntülenmesini bastırır. Bu parametre *vbc.exe* derleyicisinin [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) anahtarına karşılık gelir. |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyicinin standart kitaplıklara başvurmamasını neden olur. Bu parametre *vbc.exe* derleyicisinin [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) anahtarına karşılık gelir. |
| `NoVBRuntimeReference` | İsteğe bağlı `Boolean` parametre.<br /><br /> Yalnızca dahili kullanım. Doğruysa, *Microsoft.VisualBasic.dll'ye*otomatik başvuruyu engeller. |
| `NoWarnings` | İsteğe bağlı `Boolean` parametre.<br /><br /> If `true`, görev tüm uyarıları bastırır. Daha fazla bilgi için bkz: [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, derleyici optimizasyonları sağlar. Bu parametre *vbc.exe* derleyicisinin [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) anahtarına karşılık gelir. |
| `OptionCompare` | İsteğe bağlı `String` parametre.<br /><br /> Dize karşılaştırmalarının nasıl yapıldığını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Değer, `binary` görevin ikili dize karşılaştırmaları kullandığını belirtir. Değer, `text` görevin metin dize karşılaştırmaları kullandığını belirtir. Bu parametrenin varsayılan `binary`değeri . Bu parametre *vbc.exe* derleyicisinin [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) anahtarına karşılık gelir. |
| `OptionExplicit` | İsteğe bağlı `Boolean` parametre.<br /><br /> Değişkenlerin `true`açık beyanı gerekiyorsa. Bu parametre *vbc.exe* derleyicisinin [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) anahtarına karşılık gelir. |
| `OptionInfer` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`değişkenlerin tür çıkarım sağlar. |
| `OptionStrict` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, görev örtülü tür dönüşümleri kısıtlamak için sıkı tür semantik zorlar. Bu parametre *vbc.exe* derleyicisinin [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OptionStrictType` | İsteğe bağlı `String` parametre.<br /><br /> Hangi katı türsemanisbir uyarı oluşturur belirtir. Şu anda yalnızca "özel" desteklenir. Bu parametre *vbc.exe* derleyicisinin [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OutputAssembly` | İsteğe bağlı `String` çıktı parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Bu parametre *vbc.exe* derleyicisinin [-out](/dotnet/visual-basic/reference/command-line-compiler/out) anahtarına karşılık gelir. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyası tarafından hedeflenecek işlemci platformlarını belirtir. Bu `x86`parametre , , `x64` `Itanium`, veya `anycpu`. `anycpu` varsayılan değerdir. Bu parametre *vbc.exe* derleyicisinin [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) anahtarına karşılık gelir. |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Görevin, belirtilen maddelerden geçerli projeye ortak tür bilgilerini almasına neden olur. Bu parametre *vbc.exe* derleyicisinin [-referans](/dotnet/visual-basic/reference/command-line-compiler/reference) anahtarına karşılık gelir. |
| `RemoveIntegerChecks` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`insalı taşması hata denetimleri devre dışı. Varsayılan değer: `false`. Bu parametre *vbc.exe* derleyicisinin [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) anahtarına karşılık gelir. |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir .NET Framework kaynağını çıktı dosyasına yerle bir eder. Bu parametre *vbc.exe* derleyicisinin [-kaynak](/dotnet/visual-basic/reference/command-line-compiler/resource) anahtarına karşılık gelir. |
| `ResponseFiles` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bu görev için komutlar içeren yanıt dosyasını belirtir. Bu parametre *vbc.exe* derleyicisinin [@ (Yanıt Dosyası Belirt)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) seçeneğine karşılık gelir. |
| `RootNamespace` | İsteğe bağlı `String` parametre.<br /><br /> Tüm tür bildirimleri için kök ad alanını belirtir. Bu parametre *vbc.exe* derleyicisinin [-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) anahtarına karşılık gelir. |
| `SdkPath` | İsteğe bağlı `String` parametre.<br /><br /> *mscorlib.dll* ve *microsoft.visualbasic.dll'nin*yerini belirtir. Bu parametre *vbc.exe* derleyicisinin [-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) anahtarına karşılık gelir. |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir veya daha fazla Visual Basic kaynak dosyabelirtir. |
| `TargetCompactFramework` | İsteğe bağlı `Boolean` parametre.<br /><br /> Görev `true`.NET Compact Framework'u hedefliyorsa. Bu anahtar *vbc.exe* derleyicisinin [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) anahtarına karşılık gelir. |
| `TargetType` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir `library`konsol uygulaması oluşturan bir `exe`kod kitaplığı oluşturan `module`, bir modül oluşturan veya `winexe`bir Windows programı oluşturan bir değere sahip olabilir. `library` varsayılan değerdir. Bu parametre *vbc.exe* derleyicisinin [-hedef](/dotnet/visual-basic/reference/command-line-compiler/target) anahtarına karşılık gelir. |
| `Timeout` | İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir sonlandırıldıktan sonra milisaniye cinsinden süreyi belirtir. Varsayılan `Int.MaxValue`değer, zaman dışında bir dönem olmadığını gösterir. |
| `ToolPath` | İsteğe bağlı `String` parametre.<br /><br /> Görevin temel yürütülebilir dosyayı yükleyeceği konumu belirtir *(vbc.exe).* Bu parametre belirtilmemişse, görev MSBuild çalıştıran çerçevenin sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, tüm uyarılar hata olarak kabul edilir. Daha fazla bilgi için bkz: [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa, işlem içi derleyici nesnesini kullanma görevini bildirir. Sadece Visual Studio tarafından kullanılır. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametre.<br /><br /> UTF-8 kodlamasını kullanarak derleyici çıktısını kaydeder. Bu parametre *vbc.exe* derleyicisinin [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) anahtarına karşılık gelir. |
| `Verbosity` | İsteğe bağlı `String` parametre.<br /><br /> Derleyicinin çıktısının ayrıntılılığını belirtir. Verbosity olabilir `Quiet` `Normal` , (varsayılan), `Verbose`veya . |
| `WarningsAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak ele almak için bir uyarı listesi belirtir. Daha fazla bilgi için bkz: [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre parametreyi `TreatWarningsAsErrors` geçersiz kılar. |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak kabul edilmeyen uyarıların listesini belirtir. Daha fazla bilgi için bkz: [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre yalnızca parametre `TreatWarningsAsErrors` `true`' ye ayarlanırsa kullanışlıdır. |
| `Win32Icon` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına **Dosya Gezgini'nde**istenen görünümü veren bir *.ico* dosyasını derlemeye ekler. Bu parametre *vbc.exe* derleyicisinin [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) anahtarına karşılık gelir. |
| `Win32Resources` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına win32 kaynağı (*.res*) dosyası ekler. Bu parametre *vbc.exe* derleyicisinin [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) anahtarına karşılık gelir. |

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [ToolTaskExtension taban sınıfına](../msbuild/tooltaskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, Visual Basic projesini derler.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
