---
title: Vbc görevi | Microsoft Docs
description: MSBuild 'in, yürütülebilir dosyalar, dinamik bağlantı kitaplıkları veya kod modülleri üreten vbc.exe kaydırmak için vbc görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6596dd0893d0ab302a738cb12856fc6758df039
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908862"
---
# <a name="vbc-task"></a>Vbc görevi

Yürütülebilir dosyalar (*. exe*), dinamik bağlantı kitaplıkları (*. dll*) veya kod modülleri (*. netmodule*) üreten *vbc.exe* kaydırır. *vbc.exe* hakkında daha fazla bilgi için bkz. [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `Vbc` .

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametre.<br /><br /> Başvurular özniteliğinde belirtilen derlemelerin aranacağı ek klasörleri belirtir. |
| `AddModules` | İsteğe bağlı `String[]` parametre.<br /><br /> Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur. Bu parametre *vbc.exe* derleyicisinin [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) anahtarına karşılık gelir. |
| `BaseAddress` | İsteğe bağlı `String` parametre.<br /><br /> DLL 'nin temel adresini belirtir. Bu parametre *vbc.exe* derleyicisinin [-BaseAddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) anahtarına karşılık gelir. |
| `CodePage` | İsteğe bağlı `Int32` parametre.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu parametre *vbc.exe* derleyicisinin [-CodePage](/dotnet/visual-basic/reference/command-line-compiler/codepage) anahtarına karşılık gelir. |
| `DebugType` | İsteğe bağlı `String[]` parametre.<br /><br /> Derleyicinin hata ayıklama bilgileri oluşturmasına neden olur. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Varsayılan değer `full` , çalışan programa hata ayıklayıcı iliştirmeyi sağlar. Bir değeri, `pdbonly` program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde derleme dili kodunu görüntüler. Daha fazla bilgi için bkz. [hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | İsteğe bağlı `String[]` parametre.<br /><br /> Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimiyle belirtilir:<br /><br /> *symbol1* `=` *değer1* `;` *symbol2* `=` *değer2*<br /><br /> Bu parametre *vbc.exe* derleyicisinin [-define](/dotnet/visual-basic/reference/command-line-compiler/define) anahtarına karşılık gelir. |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev ortak anahtarı derlemeye koyar. İse `false` , görev derlemeyi tamamen imzalar. Varsayılan değer `false` . Parametresi veya parametresiyle kullanılmamışsa bu parametrenin etkisi yoktur `KeyFile` `KeyContainer` . Bu parametre *vbc.exe* derleyicisinin [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) anahtarına karşılık gelir. |
| `Deterministic` | İsteğe bağlı `Boolean` parametre.<br/><br/> İse `true` , derleyicinin özdeş olması halinde ikili içeriği derlemeler arasında özdeş olan bir derlemeyi çıkışına neden olur.<br/><br/>Daha fazla bilgi için bkz. [belirleyici](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | İsteğe bağlı `String` parametre.<br /><br /> Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının sayısal bölümünü belirtmeniz yeterlidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre *vbc.exe* derleyicisinin [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) anahtarına karşılık gelir. |
| `DocumentationFile` | İsteğe bağlı `String` parametre.<br /><br /> Belge açıklamalarını belirtilen XML dosyasına işler. Bu parametre, özniteliğini geçersiz kılar `GenerateDocumentation` . Daha fazla bilgi için bkz. [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Görev hata ayıklama bilgilerini oluşturur ve bir *. pdb* dosyasına koyar. Daha fazla bilgi için bkz. [hata ayıklama (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | İsteğe bağlı `String` parametre.<br /><br /> Görevin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> `prompt`Belirtilmişse ve bir iç derleyici hatası oluşursa, kullanıcıdan hata verilerinin Microsoft 'a gönderilmeyeceğine ilişkin bir seçenek istenir.<br /><br /> `send`Belirtilmişse ve bir iç derleyici hatası oluşursa, görev hata verilerini Microsoft 'a gönderir.<br /><br /> Varsayılan değer `none` , hataları yalnızca metin çıktısında raporlayan.<br /><br /> Bu parametre *vbc.exe* derleyicisinin [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) anahtarına karşılık gelir. |
| `FileAlignment` | İsteğe bağlı `Int32` parametre.<br /><br /> Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Bu parametre *vbc.exe* derleyicisinin [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) anahtarına karşılık gelir. |
| `GenerateDocumentation` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , belge bilgilerini oluşturur ve görevin oluşturduğu yürütülebilir dosyanın veya kitaplığın adıyla BIR XML dosyasına koyar. Daha fazla bilgi için bkz. [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Belirtilen öğe koleksiyonlarından ad alanlarını içeri aktarır. Bu parametre *vbc.exe* derleyicisinin [-Imports](/dotnet/visual-basic/reference/command-line-compiler/imports) anahtarına karşılık gelir. |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Bu parametre *vbc.exe* derleyicisinin [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) anahtarına karşılık gelir. |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> "15,5" gibi [dil sürümünü](/dotnet/visual-basic/language-reference/configure-language-version)belirtir. |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez. Bu parametre *vbc.exe* derleyicisinin [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) anahtarına karşılık gelir. |
| `MainEntryPoint` | İsteğe bağlı `String` parametre.<br /><br /> Yordamı içeren sınıfı veya modülü belirtir `Sub Main` . Bu parametre *vbc.exe* derleyicisinin [-Main](/dotnet/visual-basic/reference/command-line-compiler/main) anahtarına karşılık gelir. |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Bu modülün bir parçası olduğu derlemeyi belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyicinin *Vbc. rsp* dosyasını kullanması gerektiğini belirtir. Bu parametre, *vbc.exe* derleyicisinin [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametresine karşılık gelir. |
| `NoLogo` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici başlık bilgilerinin görüntülenmesini önler. Bu parametre *vbc.exe* derleyicisinin [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) anahtarına karşılık gelir. |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyicinin standart kitaplıklara Başvurmamasını sağlar. Bu parametre, *vbc.exe* derleyicisinin [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) anahtarına karşılık gelir. |
| `NoVBRuntimeReference` | İsteğe bağlı `Boolean` parametre.<br /><br /> Yalnızca iç kullanım. True ise *Microsoft.VisualBasic.dll* otomatik başvuruyu engeller. |
| `NoWarnings` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , görev tüm uyarıları bastırır. Daha fazla bilgi için bkz. [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici iyileştirmelerine izin vermez. Bu parametre *vbc.exe* derleyicisinin [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) anahtarına karşılık gelir. |
| `OptionCompare` | İsteğe bağlı `String` parametre.<br /><br /> Dize karşılaştırmalarının nasıl yapılacağını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Değer, `binary` görevin ikili dize karşılaştırmaları kullandığını belirtir. Değer, `text` görevin metin dizesi karşılaştırmaları kullandığını belirtir. Bu parametrenin varsayılan değeri `binary` . Bu parametre *vbc.exe* derleyicisinin [-OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) anahtarına karşılık gelir. |
| `OptionExplicit` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , değişkenlerin açık bildirimi gereklidir. Bu parametre, *vbc.exe* derleyicisinin [-OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) anahtarına karşılık gelir. |
| `OptionInfer` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , değişkenlerin tür çıkarımını izin verir. |
| `OptionStrict` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev, örtük tür dönüştürmeleri kısıtlamak için katı tür semantiğini zorlar. Bu parametre *vbc.exe* derleyicisinin [-OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OptionStrictType` | İsteğe bağlı `String` parametre.<br /><br /> Hangi katı tür semantiğinin uyarı ürettiğini belirtir. Şu anda yalnızca "Custom" desteklenir. Bu parametre *vbc.exe* derleyicisinin [-OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) anahtarına karşılık gelir. |
| `OutputAssembly` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Bu parametre *vbc.exe* derleyicisinin [Çıkış](/dotnet/visual-basic/reference/command-line-compiler/out) anahtarına karşılık gelir. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Çıkış dosyası tarafından hedeflenen işlemci platformunu belirtir. Bu parametre,,, veya değerine sahip olabilir `x86` `x64` `Itanium` `anycpu` . `anycpu` varsayılan değerdir. Bu parametre, *vbc.exe* derleyicisinin [Platform](/dotnet/visual-basic/reference/command-line-compiler/platform) anahtarına karşılık gelir. |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Görevin, belirtilen öğelerden ortak tür bilgilerini geçerli projeye almasına neden olur. Bu parametre *vbc.exe* derleyicisinin [-Reference](/dotnet/visual-basic/reference/command-line-compiler/reference) anahtarına karşılık gelir. |
| `RemoveIntegerChecks` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , tamsayı taşma hata denetimlerini devre dışı bırakır. `false` varsayılan değerdir. Bu parametre *vbc.exe* derleyicisinin [-removeintdenetimleri](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) anahtarına karşılık gelir. |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir .NET Framework kaynağını çıkış dosyasına katıştırır. Bu parametre *vbc.exe* derleyicisinin [-Resource](/dotnet/visual-basic/reference/command-line-compiler/resource) anahtarına karşılık gelir. |
| `ResponseFiles` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Bu parametre, *vbc.exe* derleyicisinin [@ (yanıt dosyasını belirt)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) seçeneğine karşılık gelir. |
| `RootNamespace` | İsteğe bağlı `String` parametre.<br /><br /> Tüm tür bildirimlerinin kök ad alanını belirtir. Bu parametre, *vbc.exe* derleyicisinin [-RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) anahtarına karşılık gelir. |
| `SdkPath` | İsteğe bağlı `String` parametre.<br /><br /> *mscorlib.dll* ve *microsoft.visualbasic.dll* konumunu belirtir. Bu parametre *vbc.exe* derleyicisinin [-SdkPath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) anahtarına karşılık gelir. |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir veya daha fazla Visual Basic kaynak dosyasını belirtir. |
| `TargetCompactFramework` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Görev, .NET Compact Framework hedefler. Bu anahtar *vbc.exe* derleyicisinin [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) anahtarına karşılık gelir. |
| `TargetType` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir, bir `library` `exe` `module` Windows programı oluşturan veya bir modül oluşturan bir konsol uygulaması oluşturan bir ' ' değeri olabilir `winexe` . `library` varsayılan değerdir. Bu parametre *vbc.exe* derleyicisinin [-target](/dotnet/visual-basic/reference/command-line-compiler/target) anahtarına karşılık gelir. |
| `Timeout` | İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue` , zaman aşımı süresi olmadığını gösterir. |
| `ToolPath` | İsteğe bağlı `String` parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (*vbc.exe*) yükleyecek konumu belirtir. Bu parametre belirtilmezse, görev MSBuild çalıştıran Framework sürümüne karşılık gelen SDK yükleme yolunu kullanır. |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , tüm uyarılar hata olarak değerlendirilir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametre.<br /><br /> Görev, varsa, işlem içi derleyici nesnesini kullanmasını söyler. Yalnızca Visual Studio tarafından kullanılır. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Bu parametre *vbc.exe* derleyicisinin [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) anahtarına karşılık gelir. |
| `Verbosity` | İsteğe bağlı `String` parametre.<br /><br /> Derleyicinin çıkışının ayrıntı düzeyini belirtir. Ayrıntı düzeyi `Quiet` , `Normal` (varsayılan) veya olabilir `Verbose` . |
| `WarningsAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirmek için uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre, parametresini geçersiz kılar `TreatWarningsAsErrors` . |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Bu parametre yalnızca `TreatWarningsAsErrors` parametresi olarak ayarlandıysa faydalıdır `true` . |
| `Win32Icon` | İsteğe bağlı `String` parametre.<br /><br /> **Dosya Gezgini**'nde, çıktı dosyasına istenen görünümü sağlayan bir *. ico* dosyasını derlemeye ekler. Bu parametre *vbc.exe* derleyicisinin [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) anahtarına karşılık gelir. |
| `Win32Resources` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına bir Win32 kaynağı (*. res*) dosyası ekler. Bu parametre *vbc.exe* derleyicisinin [-Win32Resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) anahtarına karşılık gelir. |

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
