---
title: Vbc görevi | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631243"
---
# <a name="vbc-task"></a>Vbc görevi

Yürütülebilir dosyalar ( *. exe*), dinamik bağlantı kitaplıkları ( *. dll*) veya kod modülleri ( *. netmodule*) üreten *Vbc. exe*' yi kaydırır. *Vbc. exe*hakkında daha fazla bilgi için bkz. [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `Vbc` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametresi.<br /><br /> Başvurular özniteliğinde belirtilen derlemelerin aranacağı ek klasörleri belirtir. |
| `AddModules` | İsteğe bağlı `String[]` parametresi.<br /><br /> Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur. Bu parametre, *Vbc. exe* derleyicisinin [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) anahtarına karşılık gelir. |
| `BaseAddress` | İsteğe bağlı `String` parametresi.<br /><br /> DLL 'nin temel adresini belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-BaseAddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) anahtarına karşılık gelir. |
| `CodePage` | İsteğe bağlı `Int32` parametresi.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-CodePage](/dotnet/visual-basic/reference/command-line-compiler/codepage) anahtarına karşılık gelir. |
| `DebugType` | İsteğe bağlı `String[]` parametresi.<br /><br /> Derleyicinin hata ayıklama bilgileri oluşturmasına neden olur. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Varsayılan değer, çalışan programa hata ayıklayıcı iliştirmeyi sağlayan `full`. `pdbonly` değeri, program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde derleme dili kodunu görüntüler. Daha fazla bilgi için bkz. [hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | İsteğe bağlı `String[]` parametresi.<br /><br /> Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimiyle belirtilir:<br /><br /> *symbol1* `=` *değer1* `;` *symbol2* `=` *değer2*<br /><br /> Bu parametre, *Vbc. exe* derleyicisinin [-define](/dotnet/visual-basic/reference/command-line-compiler/define) anahtarına karşılık gelir. |
| `DelaySign` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev ortak anahtarı derlemeye koyar. `false`, görev derlemeyi tamamen imzalar. Varsayılan değer `false`. Bu parametrenin `KeyFile` parametresi veya `KeyContainer` parametresiyle kullanılmadığı müddetçe hiçbir etkisi yoktur. Bu parametre, *Vbc. exe* derleyicisinin [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) anahtarına karşılık gelir. |
| `Deterministic` | İsteğe bağlı `Boolean` parametresi.<br/><br/> `true`, derleyicinin özdeş olması halinde ikili içeriği derlemeler genelinde özdeş olan bir derlemeyi çıkışına neden olur.<br/><br/>Daha fazla bilgi için bkz. [belirleyici](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | İsteğe bağlı `String` parametresi.<br /><br /> Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının sayısal bölümünü belirtmeniz yeterlidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, *Vbc. exe* derleyicisinin [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) anahtarına karşılık gelir. |
| `DocumentationFile` | İsteğe bağlı `String` parametresi.<br /><br /> Belge açıklamalarını belirtilen XML dosyasına işler. Bu parametre `GenerateDocumentation` özniteliğini geçersiz kılar. Daha fazla bilgi için bkz. [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev hata ayıklama bilgilerini oluşturur ve bir *. pdb* dosyasına koyar. Daha fazla bilgi için bkz. [hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | İsteğe bağlı `String` parametresi.<br /><br /> Görevin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> `prompt` belirtilirse ve bir iç derleyici hatası oluşursa, kullanıcıdan hata verilerinin Microsoft 'a gönderilmeyeceğine ilişkin bir seçenek istenir.<br /><br /> `send` belirtilirse ve bir iç derleyici hatası oluşursa, görev hata verilerini Microsoft 'a gönderir.<br /><br /> Varsayılan değer `none`, yalnızca metin çıkışında hata raporlar.<br /><br /> Bu parametre, *Vbc. exe* derleyicisinin [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) anahtarına karşılık gelir. |
| `FileAlignment` | İsteğe bağlı `Int32` parametresi.<br /><br /> Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Bu parametre, *Vbc. exe* derleyicisinin [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) anahtarına karşılık gelir. |
| `GenerateDocumentation` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, belge bilgilerini oluşturur ve görevin oluşturduğu yürütülebilir dosyanın veya kitaplığın adı ile bir XML dosyasına koyar. Daha fazla bilgi için bkz. [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Belirtilen öğe koleksiyonlarından ad alanlarını içeri aktarır. Bu parametre, *Vbc. exe* derleyicisinin [-Imports](/dotnet/visual-basic/reference/command-line-compiler/imports) anahtarına karşılık gelir. |
| `KeyContainer` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) anahtarına karşılık gelir. |
| `KeyFile` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> "15,5" gibi [dil sürümünü](/dotnet/visual-basic/language-reference/configure-language-version)belirtir. |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez. Bu parametre, *Vbc. exe* derleyicisinin [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) anahtarına karşılık gelir. |
| `MainEntryPoint` | İsteğe bağlı `String` parametresi.<br /><br /> `Sub Main` yordamını içeren sınıfı veya modülü belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-Main](/dotnet/visual-basic/reference/command-line-compiler/main) anahtarına karşılık gelir. |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Bu modülün bir parçası olduğu derlemeyi belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyicinin *Vbc. rsp* dosyasını kullanması gerektiğini belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametresine karşılık gelir. |
| `NoLogo` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, derleyici başlık bilgilerinin görüntülenmesini önler. Bu parametre, *Vbc. exe* derleyicisinin [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) anahtarına karşılık gelir. |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyicinin standart kitaplıklara Başvurmamasını sağlar. Bu parametre, *Vbc. exe* derleyicisinin [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) anahtarına karşılık gelir. |
| `NoVBRuntimeReference` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Yalnızca iç kullanım. Doğru ise, *Microsoft. VisualBasic. dll*' ye otomatik başvuruyu engeller. |
| `NoWarnings` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev tüm uyarıları bastırır. Daha fazla bilgi için bkz. [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, derleyici iyileştirmelerine izin vermez. Bu parametre, *Vbc. exe* derleyicisinin [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) anahtarına karşılık gelir. |
| `OptionCompare` | İsteğe bağlı `String` parametresi.<br /><br /> Dize karşılaştırmalarının nasıl yapılacağını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Değer `binary` görevin ikili dize karşılaştırmaları kullandığını belirtir. Değer `text` görevin metin dizesi karşılaştırmaları kullandığını belirtir. Bu parametrenin varsayılan değeri `binary`. Bu parametre, *Vbc. exe* derleyicisinin [-OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) anahtarına karşılık gelir. |
| `OptionExplicit` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, değişkenlerin açık bildirimi gerekir. Bu parametre, *Vbc. exe* derleyicisinin [-OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) anahtarına karşılık gelir. |
| `OptionInfer` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, değişkenlerin tür çıkarımını izin verir. |
| `OptionStrict` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev, örtük tür dönüştürmeleri kısıtlamak için katı tür semantiğini zorlar. Bu parametre, *Vbc. exe* derleyicisinin [-OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OptionStrictType` | İsteğe bağlı `String` parametresi.<br /><br /> Hangi katı tür semantiğinin uyarı ürettiğini belirtir. Şu anda yalnızca "Custom" desteklenir. Bu parametre, *Vbc. exe* derleyicisinin [-OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OutputAssembly` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [Çıkış](/dotnet/visual-basic/reference/command-line-compiler/out) anahtarına karşılık gelir. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyası tarafından hedeflenen işlemci platformunu belirtir. Bu parametre `x86`, `x64`, `Itanium`veya `anycpu`bir değere sahip olabilir. `anycpu` varsayılan değerdir. Bu parametre, *Vbc. exe* derleyicisinin [Platform](/dotnet/visual-basic/reference/command-line-compiler/platform) anahtarına karşılık gelir. |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Görevin, belirtilen öğelerden ortak tür bilgilerini geçerli projeye almasına neden olur. Bu parametre, *Vbc. exe* derleyicisinin [-Reference](/dotnet/visual-basic/reference/command-line-compiler/reference) anahtarına karşılık gelir. |
| `RemoveIntegerChecks` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, tamsayı taşma hata denetimlerini devre dışı bırakır. Varsayılan değer: `false`. Bu parametre, *Vbc. exe* derleyicisinin [-removeintdenetimleri](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) anahtarına karşılık gelir. |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir .NET Framework kaynağını çıkış dosyasına katıştırır. Bu parametre, *Vbc. exe* derleyicisinin [-Resource](/dotnet/visual-basic/reference/command-line-compiler/resource) anahtarına karşılık gelir. |
| `ResponseFiles` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [@ (yanıt dosyasını belirt)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) seçeneğine karşılık gelir. |
| `RootNamespace` | İsteğe bağlı `String` parametresi.<br /><br /> Tüm tür bildirimlerinin kök ad alanını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) anahtarına karşılık gelir. |
| `SdkPath` | İsteğe bağlı `String` parametresi.<br /><br /> *Mscorlib. dll* ve *Microsoft. VisualBasic. dll*dosyasının konumunu belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-SdkPath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) anahtarına karşılık gelir. |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir veya daha fazla Visual Basic kaynak dosyasını belirtir. |
| `TargetCompactFramework` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev .NET Compact Framework hedefler. Bu anahtar, *Vbc. exe* derleyicisinin [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) anahtarına karşılık gelir. |
| `TargetType` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre bir `library`değerine sahip olabilir, bu, bir konsol uygulaması oluşturan `exe`, bir modül oluşturan `module`, bir Windows programı oluşturan `winexe`. `library` varsayılan değerdir. Bu parametre, *Vbc. exe* derleyicisinin [-target](/dotnet/visual-basic/reference/command-line-compiler/target) anahtarına karşılık gelir. |
| `Timeout` | İsteğe bağlı `Int32` parametresi.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer, zaman aşımı süresi olmadığını belirten `Int.MaxValue`. |
| `ToolPath` | İsteğe bağlı `String` parametresi.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (*Vbc. exe*) yükleneceği konumu belirtir. Bu parametre belirtilmezse, görev MSBuild çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, tüm uyarılar hata olarak değerlendirilir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Görev, varsa, işlem içi derleyici nesnesini kullanmasını söyler. Yalnızca Visual Studio tarafından kullanılır. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Bu parametre, *Vbc. exe* derleyicisinin [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) anahtarına karşılık gelir. |
| `Verbosity` | İsteğe bağlı `String` parametresi.<br /><br /> Derleyicinin çıkışının ayrıntı düzeyini belirtir. Ayrıntı düzeyi `Quiet`, `Normal` (varsayılan) veya `Verbose`olabilir. |
| `WarningsAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirmek için uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre `TreatWarningsAsErrors` parametresini geçersiz kılar. |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre yalnızca `TreatWarningsAsErrors` parametresi `true`olarak ayarlandıysa faydalıdır. |
| `Win32Icon` | İsteğe bağlı `String` parametresi.<br /><br /> **Dosya Gezgini**'nde, çıktı dosyasına istenen görünümü sağlayan bir *. ico* dosyasını derlemeye ekler. Bu parametre, *Vbc. exe* derleyicisinin [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) anahtarına karşılık gelir. |
| `Win32Resources` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyasına bir Win32 kaynağı ( *. res*) dosyası ekler. Bu parametre, *Vbc. exe* derleyicisinin [-Win32Resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) anahtarına karşılık gelir. |

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.ToolTask> sınıfından devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek bir Visual Basic projesi derler.

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
