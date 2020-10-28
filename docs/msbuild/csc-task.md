---
title: Csc görevi | Microsoft Docs
description: Bu makalede, C# derleyicisini sarmalayan, csc.exe ve. exe,. dll veya. netmodule dosyaları üreten MSBuild Csc görevi açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16cf1c2505ad61a8c53d18d8981b8c08f9e6e02c
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796569"
---
# <a name="csc-task"></a>Csc görevi

*csc.exe* sarmalanmış ve yürütülebilir dosyalar ( *. exe* dosyaları), dinamik bağlantı kitaplıkları ( *. dll* dosyaları) veya kod modülleri ( *. netmodule* dosyaları) oluşturur. *csc.exe* hakkında daha fazla bilgi için bkz. [C# derleyici seçenekleri](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini açıklar `Csc` .

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametre.<br /><br /> Başvuruların aranacağı ek dizinleri belirtir. Daha fazla bilgi için bkz. [-lib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | İsteğe bağlı `String` parametre.<br /><br /> Derlemenin parçası olacak bir veya daha fazla modül belirtir. Daha fazla bilgi için bkz. [-addmodule (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) anahtar sözcüğünü kullanan kodu derler. Daha fazla bilgi için bkz. [-unsafe (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | İsteğe bağlı `String` parametre.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir. |
| `BaseAddress` | İsteğe bağlı `String` parametre.<br /><br /> DLL 'nin yükleneceği tercih edilen temel adresi belirtir. Bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma zamanı tarafından ayarlanır. Daha fazla bilgi için bkz. [-BaseAddress (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | İsteğe bağlı `Boolean` parametre.<br /><br /> Veri türünün sınırlarını aşan tamsayı aritmetiğinin çalışma zamanında bir özel duruma neden olup olmayacağını belirtir. Daha fazla bilgi için bkz. [checked (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | İsteğe bağlı `Int32` parametre.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Daha fazla bilgi için bkz. [-CodePage (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | İsteğe bağlı `String` parametre.<br /><br /> Hata ayıklama türünü belirtir. `DebugType` veya olabilir `full` `pdbonly` . Varsayılan değer `full` , bir hata ayıklayıcının çalışan bir programa eklenmesini sağlar. Belirleme, `pdbonly` program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamayı sağlar, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde assembler 'yi görüntüler.<br /><br /> Bu parametre, parametresini geçersiz kılar `EmitDebugInformation` .<br /><br /> Daha fazla bilgi için bkz. [-Debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | İsteğe bağlı `String` parametre.<br /><br /> Önişlemci sembolleri tanımlar. Daha fazla bilgi için bkz. [-define (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Yalnızca ortak anahtarı derlemeye yerleştirmek istediğinizi belirtir. `false`, Tam olarak imzalanan bir derleme istediğinizi belirtir<br /><br /> Ya da parametresiyle kullanılmamışsa, bu parametrenin hiçbir etkisi `KeyFile` yoktur `KeyContainer` .<br /><br /> Daha fazla bilgi için bkz. [-delaysign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | İsteğe bağlı `Boolean` parametre.<br/><br/> İse `true` , derleyicinin özdeş olması halinde ikili içeriği derlemeler arasında özdeş olan bir derlemeyi çıkışına neden olur.<br/><br/>Daha fazla bilgi için bkz. [-belirleyici (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | İsteğe bağlı `String` parametre.<br /><br /> Devre dışı bırakılacak uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-nowarn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | İsteğe bağlı `String` parametre.<br /><br /> Belge açıklamalarını bir XML dosyasına işler. Daha fazla bilgi için bkz. [-doc (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Görev hata ayıklama bilgilerini oluşturur ve bir program veritabanı (. pdb) dosyasına koyar. İse `false` , görev hata ayıklama bilgisi içermez. `false` varsayılan değerdir. Daha fazla bilgi için bkz. [-Debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | İsteğe bağlı `String` parametre.<br /><br /> , C# iç hatasını Microsoft 'a bildirmenin kolay bir yolunu sağlar. Bu parametre,, veya değerine sahip `prompt` olabilir `send` `none` . Parametresi olarak ayarlandıysa `prompt` , iç derleyici hatası oluştuğunda bir istem alırsınız. İstem bir hata raporunu Microsoft 'a elektronik olarak göndermenizi sağlar. Parametresi olarak ayarlandıysa `send` , bir hata raporu otomatik olarak gönderilir. Parametresi olarak ayarlandıysa `none` , hata yalnızca derleyicinin metin çıkışında raporlanır. `none` varsayılan değerdir. Daha fazla bilgi için bkz. [-errorreport (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | İsteğe bağlı `Int32` parametre.<br /><br /> Çıkış dosyasındaki bölümlerin boyutunu belirtir. Daha fazla bilgi için bkz. [-filealign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici çıkışında dosyanın mutlak yolunu belirtir. İse `false` , dosyanın adını belirtir. `false` varsayılan değerdir. Daha fazla bilgi için bkz. [-fullpaths (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Daha fazla bilgi için bkz. [-keycontainer (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [-keyfile (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | İsteğe bağlı `String` parametre.<br /><br /> Kullanılacak dilin sürümünü belirtir. Daha fazla bilgi için bkz. [-langversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez.<br /><br /> Bu parametreye geçirilen öğeler, ve adlı isteğe bağlı meta veri girişlerine sahip olabilir `LogicalName` `Access` . `LogicalName``identifier`anahtarın parametresine karşılık gelir `/linkresource` ve `Access` parametreye karşılık gelir `accessibility-modifier` . Daha fazla bilgi için bkz. [-linkresource (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | İsteğe bağlı `String` parametre.<br /><br /> Metodun konumunu belirtir `Main` . Daha fazla bilgi için bkz. [-Main (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Bu modülün bir parçası olacağı derlemenin adını belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyiciye *CSC. rsp* dosyası ile derlenmeyeceğini söyler. Daha fazla bilgi için bkz. [-noconfig (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici başlık bilgilerinin görüntülenmesini önler. Daha fazla bilgi için bkz. [-nologo (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Tüm sistem ad alanını tanımlayan *mscorlib.dll* içeri aktarmayı önler. Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu parametreyi kullanın. Daha fazla bilgi için bkz. [-nostdlib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Varsayılan Win32 bildirimini eklemeyin. |
| `Optimize` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` iyileştirmeleri etkinleştirilir. İse `false` iyileştirmeleri devre dışı bırakır. Daha fazla bilgi için bkz. [-optimize (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Daha fazla bilgi için bkz. [-Out (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | İsteğe bağlı `String` parametre.<br /><br /> Çıkış başvurusu derleme dosyasının adını belirtir. Daha fazla bilgi için bkz. [-refout (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | İsteğe bağlı `String` parametre.<br /><br /> Hata ayıklama bilgi dosyası adını belirtir. Varsayılan ad, *. pdb* uzantılı çıkış dosyası adıdır. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Çıkış dosyası tarafından hedeflenen işlemci platformunu belirtir. Bu parametre,, veya değerine sahip `x86` olabilir `x64` `anycpu` . `anycpu` varsayılan değerdir. Daha fazla bilgi için bkz. [-Platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Görevin, belirtilen öğelerden ortak tür bilgilerini geçerli projeye almasına neden olur. Daha fazla bilgi için bkz. [-Reference (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Özgün "başvuru" öğesine meta verileri ekleyerek bir MSBuild dosyasında C# başvuru diğer adı belirtebilirsiniz `Aliases` . Örneğin, aşağıdaki CSC komut satırında "LS1" diğer adını ayarlamak için:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Şunu kullanabilirsiniz:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir .NET Framework kaynağını çıkış dosyasına katıştırır.<br /><br /> Bu parametreye geçirilen öğeler, ve adlı isteğe bağlı meta veri girişlerine sahip olabilir `LogicalName` `Access` . `LogicalName``identifier`anahtarın parametresine karşılık gelir `/resource` ve `Access` parametreye karşılık gelir `accessibility-modifier` . Daha fazla bilgi için bkz. [-Resource (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | İsteğe bağlı `String` parametre.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir veya daha fazla C# kaynak dosyasını belirtir. |
| `TargetType` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir, bir `library` `exe` `module` Windows programı oluşturan veya bir modül oluşturan bir konsol uygulaması oluşturan bir ' ' değeri olabilir `winexe` . `library` varsayılan değerdir. Daha fazla bilgi için bkz. [-target (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , tüm uyarıları hata olarak değerlendirir. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametre.<br /><br /> Görev, varsa, işlem içi derleyici nesnesini kullanmasını söyler. Yalnızca Visual Studio tarafından kullanılır. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Daha fazla bilgi için bkz. [-utf8output (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | İsteğe bağlı `Int32` parametre.<br /><br /> Derleyicinin görüntüleyeceği uyarı düzeyini belirtir. Daha fazla bilgi için bkz. [-Warn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirmek için uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre, parametresini geçersiz kılar `TreatWarningsAsErrors` . |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre yalnızca `TreatWarningsAsErrors` parametresi olarak ayarlandıysa faydalıdır `true` . |
| `Win32Icon` | İsteğe bağlı `String` parametre.<br /><br /> **Dosya Gezgini** 'nde, çıktı dosyasına istenen görünümü sağlayan bir *. ico* dosyasını derlemeye ekler. Daha fazla bilgi için bkz. [-win32icon (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | İsteğe bağlı `String` parametre.<br /><br /> Dahil edilecek Win32 bildirimini belirtir. |
| `Win32Resource` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına bir Win32 kaynağı ( *. res* ) dosyası ekler. Daha fazla bilgi için bkz. [-win32res (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Csc` öğe koleksiyonundaki kaynak dosyalardan bir yürütülebilir dosya derlemek için görevini kullanır `Compile` .

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
