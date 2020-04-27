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
ms.openlocfilehash: 30f1a45c384495ccd02c624ea42f91a4379226df
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167462"
---
# <a name="vbc-task"></a>Vbc görevi

Yürütülebilir dosyalar (*. exe*), dinamik bağlantı kitaplıkları (*. dll*) veya kod modülleri (*. netmodule*) üreten *Vbc. exe*' yi kaydırır. *Vbc. exe*hakkında daha fazla bilgi için bkz. [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, `Vbc` görevin parametrelerini açıklar.

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe `String[]` bağlı parametre.<br /><br /> Başvurular özniteliğinde belirtilen derlemelerin aranacağı ek klasörleri belirtir. |
| `AddModules` | İsteğe `String[]` bağlı parametre.<br /><br /> Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur. Bu parametre, *Vbc. exe* derleyicisinin [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) anahtarına karşılık gelir. |
| `BaseAddress` | İsteğe `String` bağlı parametre.<br /><br /> DLL 'nin temel adresini belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-BaseAddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) anahtarına karşılık gelir. |
| `CodePage` | İsteğe `Int32` bağlı parametre.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-CodePage](/dotnet/visual-basic/reference/command-line-compiler/codepage) anahtarına karşılık gelir. |
| `DebugType` | İsteğe `String[]` bağlı parametre.<br /><br /> Derleyicinin hata ayıklama bilgileri oluşturmasına neden olur. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Varsayılan değer `full`, çalışan programa hata ayıklayıcı iliştirmeyi sağlar. Bir değeri, `pdbonly` program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde derleme dili kodunu görüntüler. Daha fazla bilgi için bkz. [hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | İsteğe `String[]` bağlı parametre.<br /><br /> Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimiyle belirtilir:<br /><br /> *symbol1* `=` *value1* değer1 `;` *symbol2* symbol2 `=` *değer2*<br /><br /> Bu parametre, *Vbc. exe* derleyicisinin [-define](/dotnet/visual-basic/reference/command-line-compiler/define) anahtarına karşılık gelir. |
| `DelaySign` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, görev ortak anahtarı derlemeye koyar. İse `false`, görev derlemeyi tamamen imzalar. Varsayılan değer `false`. Parametresi veya `KeyFile` `KeyContainer` parametresiyle kullanılmamışsa bu parametrenin etkisi yoktur. Bu parametre, *Vbc. exe* derleyicisinin [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) anahtarına karşılık gelir. |
| `Deterministic` | İsteğe `Boolean` bağlı parametre.<br/><br/> İse `true`, derleyicinin özdeş olması halinde ikili içeriği derlemeler arasında özdeş olan bir derlemeyi çıkışına neden olur.<br/><br/>Daha fazla bilgi için bkz. [belirleyici](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | İsteğe `String` bağlı parametre.<br /><br /> Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının sayısal bölümünü belirtmeniz yeterlidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre, *Vbc. exe* derleyicisinin [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) anahtarına karşılık gelir. |
| `DocumentationFile` | İsteğe `String` bağlı parametre.<br /><br /> Belge açıklamalarını belirtilen XML dosyasına işler. Bu parametre, `GenerateDocumentation` özniteliğini geçersiz kılar. Daha fazla bilgi için bkz. [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | İsteğe `Boolean` bağlı parametre.<br /><br /> `true`Görev hata ayıklama bilgilerini oluşturur ve bir *. pdb* dosyasına koyar. Daha fazla bilgi için bkz. [hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | İsteğe `String` bağlı parametre.<br /><br /> Görevin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> `prompt` Belirtilmişse ve bir iç derleyici hatası oluşursa, kullanıcıdan hata verilerinin Microsoft 'a gönderilmeyeceğine ilişkin bir seçenek istenir.<br /><br /> `send` Belirtilmişse ve bir iç derleyici hatası oluşursa, görev hata verilerini Microsoft 'a gönderir.<br /><br /> Varsayılan değer `none`, hataları yalnızca metin çıktısında raporlayan.<br /><br /> Bu parametre, *Vbc. exe* derleyicisinin [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) anahtarına karşılık gelir. |
| `FileAlignment` | İsteğe `Int32` bağlı parametre.<br /><br /> Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Bu parametre, *Vbc. exe* derleyicisinin [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) anahtarına karşılık gelir. |
| `GenerateDocumentation` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, belge bilgilerini oluşturur ve görevin oluşturduğu yürütülebilir dosyanın veya kitaplığın ADıYLA bir XML dosyasına koyar. Daha fazla bilgi için bkz. [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Belirtilen öğe koleksiyonlarından ad alanlarını içeri aktarır. Bu parametre, *Vbc. exe* derleyicisinin [-Imports](/dotnet/visual-basic/reference/command-line-compiler/imports) anahtarına karşılık gelir. |
| `KeyContainer` | İsteğe `String` bağlı parametre.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) anahtarına karşılık gelir. |
| `KeyFile` | İsteğe `String` bağlı parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | İsteğe <xref:System.String?displayProperty=fullName> bağlı parametre.<br /><br /> "15,5" gibi [dil sürümünü](/dotnet/visual-basic/language-reference/configure-language-version)belirtir. |
| `LinkResources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez. Bu parametre, *Vbc. exe* derleyicisinin [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) anahtarına karşılık gelir. |
| `MainEntryPoint` | İsteğe `String` bağlı parametre.<br /><br /> `Sub Main` Yordamı içeren sınıfı veya modülü belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-Main](/dotnet/visual-basic/reference/command-line-compiler/main) anahtarına karşılık gelir. |
| `ModuleAssemblyName` | İsteğe `String` bağlı parametre.<br /><br /> Bu modülün bir parçası olduğu derlemeyi belirtir. |
| `NoConfig` | İsteğe `Boolean` bağlı parametre.<br /><br /> Derleyicinin *Vbc. rsp* dosyasını kullanması gerektiğini belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametresine karşılık gelir. |
| `NoLogo` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, derleyici başlık bilgilerinin görüntülenmesini önler. Bu parametre, *Vbc. exe* derleyicisinin [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) anahtarına karşılık gelir. |
| `NoStandardLib` | İsteğe `Boolean` bağlı parametre.<br /><br /> Derleyicinin standart kitaplıklara Başvurmamasını sağlar. Bu parametre, *Vbc. exe* derleyicisinin [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) anahtarına karşılık gelir. |
| `NoVBRuntimeReference` | İsteğe `Boolean` bağlı parametre.<br /><br /> Yalnızca iç kullanım. Doğru ise, *Microsoft. VisualBasic. dll*' ye otomatik başvuruyu engeller. |
| `NoWarnings` | İsteğe `Boolean` bağlı parametre.<br /><br /> Varsa `true`, görev tüm uyarıları bastırır. Daha fazla bilgi için bkz. [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, derleyici iyileştirmelerine izin vermez. Bu parametre, *Vbc. exe* derleyicisinin [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) anahtarına karşılık gelir. |
| `OptionCompare` | İsteğe `String` bağlı parametre.<br /><br /> Dize karşılaştırmalarının nasıl yapılacağını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Değer `binary` , görevin ikili dize karşılaştırmaları kullandığını belirtir. Değer `text` , görevin metin dizesi karşılaştırmaları kullandığını belirtir. Bu parametrenin varsayılan değeri `binary`. Bu parametre, *Vbc. exe* derleyicisinin [-OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) anahtarına karşılık gelir. |
| `OptionExplicit` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, değişkenlerin açık bildirimi gereklidir. Bu parametre, *Vbc. exe* derleyicisinin [-OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) anahtarına karşılık gelir. |
| `OptionInfer` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, değişkenlerin tür çıkarımını izin verir. |
| `OptionStrict` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, görev, örtük tür dönüştürmeleri kısıtlamak için katı tür semantiğini zorlar. Bu parametre, *Vbc. exe* derleyicisinin [-OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OptionStrictType` | İsteğe `String` bağlı parametre.<br /><br /> Hangi katı tür semantiğinin uyarı ürettiğini belirtir. Şu anda yalnızca "Custom" desteklenir. Bu parametre, *Vbc. exe* derleyicisinin [-OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OutputAssembly` | İsteğe `String` bağlı çıkış parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [Çıkış](/dotnet/visual-basic/reference/command-line-compiler/out) anahtarına karşılık gelir. |
| `Platform` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış dosyası tarafından hedeflenen işlemci platformunu belirtir. Bu parametre `x86`, `x64` `Itanium`,, veya `anycpu`değerine sahip olabilir. `anycpu` varsayılan değerdir. Bu parametre, *Vbc. exe* derleyicisinin [Platform](/dotnet/visual-basic/reference/command-line-compiler/platform) anahtarına karşılık gelir. |
| `References` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Görevin, belirtilen öğelerden ortak tür bilgilerini geçerli projeye almasına neden olur. Bu parametre, *Vbc. exe* derleyicisinin [-Reference](/dotnet/visual-basic/reference/command-line-compiler/reference) anahtarına karşılık gelir. |
| `RemoveIntegerChecks` | İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, tamsayı taşma hata denetimlerini devre dışı bırakır. Varsayılan değer: `false`. Bu parametre, *Vbc. exe* derleyicisinin [-removeintdenetimleri](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) anahtarına karşılık gelir. |
| `Resources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bir .NET Framework kaynağını çıkış dosyasına katıştırır. Bu parametre, *Vbc. exe* derleyicisinin [-Resource](/dotnet/visual-basic/reference/command-line-compiler/resource) anahtarına karşılık gelir. |
| `ResponseFiles` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [@ (yanıt dosyasını belirt)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) seçeneğine karşılık gelir. |
| `RootNamespace` | İsteğe `String` bağlı parametre.<br /><br /> Tüm tür bildirimlerinin kök ad alanını belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) anahtarına karşılık gelir. |
| `SdkPath` | İsteğe `String` bağlı parametre.<br /><br /> *Mscorlib. dll* ve *Microsoft. VisualBasic. dll*dosyasının konumunu belirtir. Bu parametre, *Vbc. exe* derleyicisinin [-SdkPath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) anahtarına karşılık gelir. |
| `Sources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bir veya daha fazla Visual Basic kaynak dosyasını belirtir. |
| `TargetCompactFramework` | İsteğe `Boolean` bağlı parametre.<br /><br /> `true`Görev, .NET Compact Framework hedefler. Bu anahtar, *Vbc. exe* derleyicisinin [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) anahtarına karşılık gelir. |
| `TargetType` | İsteğe `String` bağlı parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir, bir Windows `library`programı oluşturan veya `winexe`bir modül oluşturan bir `exe`konsol uygulaması `module`oluşturan bir ' ' değeri olabilir. `library` varsayılan değerdir. Bu parametre, *Vbc. exe* derleyicisinin [-target](/dotnet/visual-basic/reference/command-line-compiler/target) anahtarına karşılık gelir. |
| `Timeout` | İsteğe `Int32` bağlı parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue`, zaman aşımı süresi olmadığını gösterir. |
| `ToolPath` | İsteğe `String` bağlı parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (*Vbc. exe*) yükleneceği konumu belirtir. Bu parametre belirtilmezse, görev MSBuild çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `TreatWarningsAsErrors` | İsteğe `Boolean` bağlı parametre.<br /><br /> Varsa `true`, tüm uyarılar hata olarak değerlendirilir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | İsteğe `Boolean` bağlı parametre.<br /><br /> Görev, varsa, işlem içi derleyici nesnesini kullanmasını söyler. Yalnızca Visual Studio tarafından kullanılır. |
| `Utf8Output` | İsteğe `Boolean` bağlı parametre.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Bu parametre, *Vbc. exe* derleyicisinin [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) anahtarına karşılık gelir. |
| `Verbosity` | İsteğe `String` bağlı parametre.<br /><br /> Derleyicinin çıkışının ayrıntı düzeyini belirtir. Ayrıntı düzeyi `Quiet`, `Normal` (varsayılan) veya `Verbose`olabilir. |
| `WarningsAsErrors` | İsteğe `String` bağlı parametre.<br /><br /> Hata olarak değerlendirmek için uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre, `TreatWarningsAsErrors` parametresini geçersiz kılar. |
| `WarningsNotAsErrors` | İsteğe `String` bağlı parametre.<br /><br /> Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre yalnızca `TreatWarningsAsErrors` parametresi olarak `true`ayarlandıysa faydalıdır. |
| `Win32Icon` | İsteğe `String` bağlı parametre.<br /><br /> **Dosya Gezgini**'nde, çıktı dosyasına istenen görünümü sağlayan bir *. ico* dosyasını derlemeye ekler. Bu parametre, *Vbc. exe* derleyicisinin [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) anahtarına karşılık gelir. |
| `Win32Resources` | İsteğe `String` bağlı parametre.<br /><br /> Çıktı dosyasına bir Win32 kaynağı (*. res*) dosyası ekler. Bu parametre, *Vbc. exe* derleyicisinin [-Win32Resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) anahtarına karşılık gelir. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

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
