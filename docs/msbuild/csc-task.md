---
title: Csc görevi | Microsoft Docs
description: bu makalede, C# derleyicisini sarmalayan, csc.exe ve .exe, .dll veya. netmodule dosyaları üreten MSBuild Csc görevi açıklanmaktadır.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: cae7ff3a8c413051e38d9a6c5209717d1b5b481f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123430"
---
# <a name="csc-task"></a>Csc görevi

*csc.exe* sarmalanmış ve yürütülebilir dosyalar (*.exe* dosyaları), dinamik bağlantı kitaplıkları (*.dll* dosyaları) veya kod modülleri (*. netmodule* dosyaları) oluşturur. *csc.exe* hakkında daha fazla bilgi için bkz. [C# derleyici seçenekleri](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini açıklar `Csc` .

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametre.<br /><br /> Başvuruların aranacağı ek dizinleri belirtir. Daha fazla bilgi için bkz. [-lib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | İsteğe bağlı `String` parametre.<br /><br /> Derlemenin parçası olacak bir veya daha fazla modül belirtir. Daha fazla bilgi için bkz. [-addmodule (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) anahtar sözcüğünü kullanan kodu derler. Daha fazla bilgi için bkz. [-unsafe (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | İsteğe bağlı `String` parametre.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir. |
| `BaseAddress` | İsteğe bağlı `String` parametre.<br /><br /> DLL 'nin yükleneceği tercih edilen temel adresi belirtir. bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma zamanı tarafından ayarlanır. Daha fazla bilgi için bkz. [-BaseAddress (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | İsteğe bağlı `Boolean` parametre.<br /><br /> Veri türünün sınırlarını aşan tamsayı aritmetiğinin çalışma zamanında bir özel duruma neden olup olmayacağını belirtir. Daha fazla bilgi için bkz. [checked (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | İsteğe bağlı `Int32` parametre.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Daha fazla bilgi için bkz. [-CodePage (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | İsteğe bağlı `String` parametre.<br /><br /> Hata ayıklama türünü belirtir. `DebugType` veya olabilir `full` `pdbonly` . Varsayılan değer `full` , bir hata ayıklayıcının çalışan bir programa eklenmesini sağlar. Belirleme, `pdbonly` program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamayı sağlar, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde assembler 'yi görüntüler.<br /><br /> Bu parametre, parametresini geçersiz kılar `EmitDebugInformation` .<br /><br /> Daha fazla bilgi için bkz. [-Debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | İsteğe bağlı `String` parametre.<br /><br /> Önişlemci sembolleri tanımlar. Daha fazla bilgi için bkz. [-define (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Yalnızca ortak anahtarı derlemeye yerleştirmek istediğinizi belirtir. `false`, Tam olarak imzalanan bir derleme istediğinizi belirtir<br /><br /> Ya da parametresiyle kullanılmamışsa, bu parametrenin hiçbir etkisi `KeyFile` yoktur `KeyContainer` .<br /><br /> Daha fazla bilgi için bkz. [-delaysign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | İsteğe bağlı `Boolean` parametre.<br/><br/> İse `true` , derleyicinin özdeş olması halinde ikili içeriği derlemeler arasında özdeş olan bir derlemeyi çıkışına neden olur.<br/><br/>Daha fazla bilgi için bkz. [-belirleyici (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | İsteğe bağlı `String` parametre.<br /><br /> Devre dışı bırakılacak uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-nowarn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | İsteğe bağlı `String` parametre.<br /><br /> Belge açıklamalarını bir XML dosyasına işler. Daha fazla bilgi için bkz. [-doc (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmbedAllSources` | İsteğe bağlı `Boolean` parametre.<br /><br /> Tüm kaynak dosyalarını PDB 'ye ekleyin. Daha fazla bilgi için bkz. [-embed (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically) |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Görev hata ayıklama bilgilerini oluşturur ve bir program veritabanı (. pdb) dosyasına koyar. İse `false` , görev hata ayıklama bilgisi içermez. `false` varsayılan değerdir. Daha fazla bilgi için bkz. [-Debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | İsteğe bağlı `String` parametre.<br /><br /> , C# iç hatasını Microsoft 'a bildirmenin kolay bir yolunu sağlar. Bu parametre,, veya değerine sahip `prompt` olabilir `send` `none` . Parametresi olarak ayarlandıysa `prompt` , iç derleyici hatası oluştuğunda bir istem alırsınız. İstem bir hata raporunu Microsoft 'a elektronik olarak göndermenizi sağlar. Parametresi olarak ayarlandıysa `send` , bir hata raporu otomatik olarak gönderilir. Parametresi olarak ayarlandıysa `none` , hata yalnızca derleyicinin metin çıkışında raporlanır. `none` varsayılan değerdir. Daha fazla bilgi için bkz. [-errorreport (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | İsteğe bağlı `Int32` parametre.<br /><br /> Çıkış dosyasındaki bölümlerin boyutunu belirtir. Daha fazla bilgi için bkz. [-filealign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici çıkışında dosyanın mutlak yolunu belirtir. İse `false` , dosyanın adını belirtir. `false` varsayılan değerdir. Daha fazla bilgi için bkz. [-fullpaths (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Daha fazla bilgi için bkz. [-keycontainer (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [-keyfile (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | İsteğe bağlı `String` parametre.<br /><br /> Kullanılacak dilin sürümünü belirtir. Daha fazla bilgi için bkz. [-langversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez.<br /><br /> Bu parametreye geçirilen öğeler, ve adlı isteğe bağlı meta veri girişlerine sahip olabilir `LogicalName` `Access` . `LogicalName``identifier`anahtarın parametresine karşılık gelir `/linkresource` ve `Access` parametreye karşılık gelir `accessibility-modifier` . Daha fazla bilgi için bkz. [-linkresource (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | İsteğe bağlı `String` parametre.<br /><br /> Metodun konumunu belirtir `Main` . Daha fazla bilgi için bkz. [-Main (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Bu modülün bir parçası olacağı derlemenin adını belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyiciye *CSC. rsp* dosyası ile derlenmeyeceğini söyler. Daha fazla bilgi için bkz. [-noconfig (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` derleyici başlık bilgisinin görüntülenmez. Daha fazla bilgi için bkz. [-nologo (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | İsteğe `Boolean` bağlı parametre.<br /><br /> , `true` tüm Sistem ad alanını tanımlayan *mscorlib.dll* için içeri aktarmayı önler. Kendi Sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak için bu parametreyi kullanın. Daha fazla bilgi için bkz. [-nostdlib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` varsayılan Win32 bildirimini dahil değildir. |
| `Optimize` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` iyileştirmeleri sağlar. ise, `false` iyileştirmeleri devre dışı gösterir. Daha fazla bilgi için bkz. [-optimize (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | İsteğe `String` bağlı çıkış parametresi.<br /><br /> Çıkış dosyasının adını belirtir. Daha fazla bilgi için bkz. [-out (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış başvurusu derleme dosyasının adını belirtir. Daha fazla bilgi için bkz. [-refout (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | İsteğe `String` bağlı parametre.<br /><br /> Hata ayıklama bilgileri dosya adını belirtir. Varsayılan ad, *.pdb* uzantısına sahip çıkış dosyası adıdır. |
| `Platform` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış dosyası tarafından hedeflen işlemci platformunu belirtir. Bu parametre , veya `x86` `x64` değerine sahip `anycpu` olabilir. `anycpu` varsayılan değerdir. Daha fazla bilgi için bkz. [-platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Görevin belirtilen öğelerden ortak tür bilgilerini geçerli projeye içeri aktarmasına neden olur. Daha fazla bilgi için [bkz. -reference (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Meta verileri özgün "Başvuru" öğeye ekleyerek MSBuild bir C# `Aliases` başvuru diğer adı belirtebilirsiniz. Örneğin, aşağıdaki Csc komut satırına "LS1" diğer adını ayarlamak için:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> şunları kullanabilirsiniz:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Çıkış dosyasına .NET Framework bir kaynak katıştırır.<br /><br /> Bu parametreye geçirilen öğelerin ve adlı isteğe bağlı meta veri girdileri `LogicalName` `Access` olabilir. `LogicalName` anahtarının `identifier` parametresine `/resource` ve `Access` parametresine karşılık gelen bir `accessibility-modifier` değerdir. Daha fazla bilgi için [bkz. -resource (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | İsteğe `String` bağlı parametre.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Daha fazla bilgi için [bkz. @ (Yanıt dosyasını belirtin)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bir veya daha fazla C# kaynak dosyası belirtir. |
| `TargetType` | İsteğe `String` bağlı parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir modül veya bir konsol programı oluşturan bir konsol uygulaması oluşturan bir kod kitaplığı oluşturan bir değerine sahip `library` `exe` Windows `module` `winexe` olabilir. `library` varsayılan değerdir. Daha fazla bilgi için [bkz. -target (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` tüm uyarıları hata olarak davranır. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | İsteğe `Boolean` bağlı parametre.<br /><br /> Varsa, göreve işlem içinde derleyici nesnesini kullanma talimatı sağlar. Yalnızca Visual Studio. |
| `Utf8Output` | İsteğe `Boolean` bağlı parametre.<br /><br /> UTF-8 kodlamasını kullanarak derleyici çıktısını günlüğe kaydeder. Daha fazla bilgi için bkz. [-utf8output (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | İsteğe `Int32` bağlı parametre.<br /><br /> Derleyicinin görüntülediği uyarı düzeyini belirtir. Daha fazla bilgi için [bkz. -warn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | İsteğe `String` bağlı parametre.<br /><br /> Hata olarak davranan uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre, parametresini geçersiz `TreatWarningsAsErrors` kılar. |
| `WarningsNotAsErrors` | İsteğe `String` bağlı parametre.<br /><br /> Hata olarak kabul edilen uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre yalnızca parametresi olarak `TreatWarningsAsErrors` ayarlanmışsa `true` kullanışlıdır. |
| `Win32Icon` | İsteğe `String` bağlı parametre.<br /><br /> Derlemeye *bir .ico* dosyası ekler ve bu da çıkış dosyasına dosyanın içinde istenen **Dosya Gezgini.** Daha fazla bilgi için bkz. [-win32icon (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | İsteğe `String` bağlı parametre.<br /><br /> Eklenecek Win32 bildirimini belirtir. |
| `Win32Resource` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış dosyasına bir Win32 kaynak (*.res*) dosyası ekler. Daha fazla bilgi için bkz. [-win32res (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğe `Csc` koleksiyonunda kaynak dosyalardan yürütülebilir bir derlemek için `Compile` görevini kullanır.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
