---
title: Csc Görev | Microsoft Docs
description: Bu makalede C# derleyicisi, csc.exe sarmalayıcı ve .exe, .dll veya .netmodule dosyaları üreten MSBuild Csc görevi açıklanmıştır.
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
ms.workload:
- multiple
ms.openlocfilehash: 10a63b114379f56ca5f253f853a1ff6bdd6c60dc
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588481"
---
# <a name="csc-task"></a>Csc görevi

, *csc.exe* sarmalar ve *yürütülebilir dosyalar* (.exedosyaları), dinamik bağlantı kitaplıkları (*.dll* dosyaları) veya kod modülleri (*.netmodule* dosyaları) üretir. hakkında daha fazla bilgi *csc.exe* bkz. [C# derleyici seçenekleri.](/dotnet/csharp/language-reference/compiler-options/index)

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `Csc` almaktadır.

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe `String[]` bağlı parametre.<br /><br /> Başvurular için arama yapmak için ek dizinler belirtir. Daha fazla bilgi için bkz. [-lib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | İsteğe `String` bağlı parametre.<br /><br /> Derlemenin parçası olacak bir veya daha fazla modülü belirtir. Daha fazla bilgi için [bkz. -addmodule (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` güvenli olmayan anahtar sözcüğünü kullanan kodu [derler.](/dotnet/csharp/language-reference/keywords/unsafe) Daha fazla bilgi için [bkz. -unsafe (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | İsteğe `String` bağlı parametre.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir. |
| `BaseAddress` | İsteğe `String` bağlı parametre.<br /><br /> BIR DLL'nin yük yüklemek için tercih edilen temel adresi belirtir. BIR DLL için varsayılan temel adres, ortak dil çalışma .NET Framework tarafından ayarlanır. Daha fazla bilgi için bkz. [-baseaddress (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | İsteğe `Boolean` bağlı parametre.<br /><br /> Veri türünün sınırlarına taşan tamsayı aritmetiğinin çalışma zamanında özel durumlara neden olup olmadığını belirtir. Daha fazla bilgi için bkz. [-checked (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | İsteğe `Int32` bağlı parametre.<br /><br /> Derlemede tüm kaynak kod dosyaları için kullanmak üzere kod sayfasını belirtir. Daha fazla bilgi için bkz. [-codepage (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | İsteğe `String` bağlı parametre.<br /><br /> Hata ayıklama türünü belirtir. `DebugType` veya `full` `pdbonly` olabilir. Varsayılan değer, `full` bir hata ayıklayıcının çalışan bir programa bağlanmasını sağlayan 'tır. belirterek, program hata ayıklayıcıda başlatıcıda kaynak kodunda hata ayıklamayı sağlar, ancak yalnızca çalışan program hata ayıklayıcıya ekli `pdbonly` olduğunda assembler'ı görüntüler.<br /><br /> Bu parametre, parametresini geçersiz `EmitDebugInformation` kılar.<br /><br /> Daha fazla bilgi için [bkz. -debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | İsteğe `String` bağlı parametre.<br /><br /> Ön işlemci sembollerini tanımlar. Daha fazla bilgi için [bkz. -define (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | İsteğe `Boolean` bağlı parametre.<br /><br /> `true`ise, ortak anahtarı yalnızca derlemeye yer almak istediğiniz belirtir. ise, `false` tam olarak imzalanmış bir derleme istediğinizi belirtir<br /><br /> veya parametresiyle kullanılmadıkça bu parametrenin `KeyFile` hiçbir etkisi `KeyContainer` olmaz.<br /><br /> Daha fazla bilgi için bkz. [-delaysign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | İsteğe `Boolean` bağlı parametre.<br/><br/> ise, girişler aynı ise, derleyicinin derlemeler arasında ikili içeriği aynı olan bir `true` derleme çıkışına neden olur.<br/><br/>Daha fazla bilgi için [bkz. -deterministic (C# Derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | İsteğe `String` bağlı parametre.<br /><br /> Devre dışı bırakılacak uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-nowarn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | İsteğe `String` bağlı parametre.<br /><br /> Belge açıklamalarını bir XML dosyasına işler. Daha fazla bilgi için [bkz. -doc (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmbedAllSources` | İsteğe `Boolean` bağlı parametre.<br /><br /> Tüm kaynak dosyaları PDB'ye ekleme. Daha fazla bilgi için [bkz. -embed (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically) |
| `EmitDebugInformation` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, görev hata ayıklama bilgileri oluşturur ve bunu bir `true` program veritabanı (.pdb) dosyasına yer verir. ise, `false` görev hiçbir hata ayıklama bilgisi yaymaz. `false` varsayılan değerdir. Daha fazla bilgi için [bkz. -debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | İsteğe `String` bağlı parametre.<br /><br /> C# iç hatasını Microsoft'a bildirmenin kullanışlı bir yolunu sağlar. Bu parametre , veya `prompt` `send` değerine sahip `none` olabilir. parametresi olarak `prompt` ayarlanırsa, iç derleyici hatası oluştuğunda bir istem alırsınız. İstem, Hata raporunu Microsoft'a elektronik olarak göndermenizi sağlar. parametresi olarak ayarlanırsa `send` otomatik olarak bir hata raporu gönderilir. parametresi olarak `none` ayarlanırsa, hata yalnızca derleyicinin metin çıkışında raporlandı. `none` varsayılan değerdir. Daha fazla bilgi için bkz. [-errorreport (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | İsteğe `Int32` bağlı parametre.<br /><br /> Çıkış dosyasındaki bölümlerin boyutunu belirtir. Daha fazla bilgi için bkz. [-filealign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` derleyici çıkışında dosyanın mutlak yolunu belirtir. ise, `false` dosyanın adını belirtir. `false` varsayılan değerdir. Daha fazla bilgi için bkz. [-fullpaths (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | İsteğe `String` bağlı parametre.<br /><br /> Şifreleme anahtarı kapsayıcının adını belirtir. Daha fazla bilgi için bkz. [-keycontainer (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | İsteğe `String` bağlı parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [-keyfile (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | İsteğe `String` bağlı parametre.<br /><br /> Kullanmak için dilin sürümünü belirtir. Daha fazla bilgi için bkz. [-langversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Çıkış dosyasında bir .NET Framework bağlantısı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmaz.<br /><br /> Bu parametreye geçirilen öğelerin ve adlı isteğe bağlı meta veri girdileri `LogicalName` `Access` olabilir. `LogicalName` anahtarının `identifier` parametresine `/linkresource` ve `Access` parametresine karşılık gelen bir `accessibility-modifier` değerdir. Daha fazla bilgi için bkz. [-linkresource (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | İsteğe `String` bağlı parametre.<br /><br /> Yönteminin konumunu `Main` belirtir. Daha fazla bilgi için bkz. [-main (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | İsteğe `String` bağlı parametre.<br /><br /> Bu modülün bir parçası olacak derlemenin adını belirtir. |
| `NoConfig` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` derleyiciye *csc.rsp dosyasıyla derlenem olmadığını* söyler. Daha fazla bilgi için bkz. [-noconfig (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` derleyici başlık bilgisinin görüntülenmez. Daha fazla bilgi için bkz. [-nologo (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | İsteğe `Boolean` bağlı parametre.<br /><br /> , `true` tüm Sistem ad alanını tanımlayan *mscorlib.dll* için içeri aktarmayı önler. Kendi Sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak için bu parametreyi kullanın. Daha fazla bilgi için bkz. [-nostdlib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` varsayılan Win32 bildirimini dahil değildir. |
| `Optimize` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` iyileştirmeleri sağlar. ise, `false` iyileştirmeleri devre dışı gösterir. Daha fazla bilgi için bkz. [-optimize (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | İsteğe `String` bağlı çıkış parametresi.<br /><br /> Çıkış dosyasının adını belirtir. Daha fazla bilgi için bkz. [-out (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış başvurusu derleme dosyasının adını belirtir. Daha fazla bilgi için bkz. [-refout (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | İsteğe `String` bağlı parametre.<br /><br /> Hata ayıklama bilgileri dosya adını belirtir. Varsayılan ad, *.pdb* uzantısına sahip çıkış dosyası adıdır. |
| `Platform` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış dosyası tarafından hedeflen işlemci platformunu belirtir. Bu parametre , veya `x86` `x64` değerine sahip `anycpu` olabilir. `anycpu` varsayılan değerdir. Daha fazla bilgi için bkz. [-platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Görevin belirtilen öğelerden ortak tür bilgilerini geçerli projeye içeri aktarmasına neden olur. Daha fazla bilgi için [bkz. -reference (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Meta verileri özgün "Başvuru" öğeye ekleyerek MSBuild dosyasında bir C# `Aliases` başvuru diğer adı belirtebilirsiniz. Örneğin, aşağıdaki Csc komut satırına "LS1" diğer adını ayarlamak için:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> şunları kullanabilirsiniz:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Çıkış dosyasına .NET Framework bir kaynak katıştırır.<br /><br /> Bu parametreye geçirilen öğelerin ve adlı isteğe bağlı meta veri girdileri `LogicalName` `Access` olabilir. `LogicalName` anahtarının `identifier` parametresine `/resource` ve `Access` parametresine karşılık gelen bir `accessibility-modifier` değerdir. Daha fazla bilgi için [bkz. -resource (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | İsteğe `String` bağlı parametre.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Daha fazla bilgi için [bkz. @ (Yanıt dosyasını belirtin)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bir veya daha fazla C# kaynak dosyası belirtir. |
| `TargetType` | İsteğe `String` bağlı parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir modül veya bir Windows programı oluşturan bir konsol uygulaması oluşturan bir kod kitaplığı oluşturan `library` `exe` `module` `winexe` değerine sahip olabilir. `library` varsayılan değerdir. Daha fazla bilgi için [bkz. -target (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` tüm uyarıları hata olarak davranır. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | İsteğe `Boolean` bağlı parametre.<br /><br /> Varsa, göreve işlem içinde derleyici nesnesini kullanma talimatı sağlar. Yalnızca Visual Studio. |
| `Utf8Output` | İsteğe `Boolean` bağlı parametre.<br /><br /> UTF-8 kodlamasını kullanarak derleyici çıktısını günlüğe kaydeder. Daha fazla bilgi için bkz. [-utf8output (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | İsteğe `Int32` bağlı parametre.<br /><br /> Derleyicinin görüntülediği uyarı düzeyini belirtir. Daha fazla bilgi için [bkz. -warn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | İsteğe `String` bağlı parametre.<br /><br /> Hata olarak davranan uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre, parametresini geçersiz `TreatWarningsAsErrors` kılar. |
| `WarningsNotAsErrors` | İsteğe `String` bağlı parametre.<br /><br /> Hata olarak kabul edilen uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre yalnızca parametresi olarak `TreatWarningsAsErrors` ayarlanmışsa `true` kullanışlıdır. |
| `Win32Icon` | İsteğe `String` bağlı parametre.<br /><br /> Derlemeye *bir .ico* dosyası ekler ve bu da çıkış dosyasına dosyanın içinde istenen **görünümü Dosya Gezgini.** Daha fazla bilgi için bkz. [-win32icon (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | İsteğe `String` bağlı parametre.<br /><br /> Eklenecek Win32 bildirimini belirtir. |
| `Win32Resource` | İsteğe `String` bağlı parametre.<br /><br /> Çıkış dosyasına bir Win32 kaynak (*.res*) dosyası ekler. Daha fazla bilgi için bkz. [-win32res (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğe `Csc` koleksiyonunda kaynak dosyalardan yürütülebilir dosya derlemek için `Compile` görevini kullanır.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
