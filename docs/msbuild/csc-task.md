---
title: Csc Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 3c88e5aaef9262d320cdf61564078246dee46b10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634272"
---
# <a name="csc-task"></a>Csc görevi

*csc.exe'yi*sarar ve yürütülebilir dosyalar (*.exe* dosyaları), dinamik bağlantı kitaplıklarını (*.dll* dosyaları) veya kod modüllerini *(.netmodule* dosyaları) sarar. *csc.exe*hakkında daha fazla bilgi için [C# derleyici seçeneklerine](/dotnet/csharp/language-reference/compiler-options/index)bakın.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevparametreleri `Csc` açıklanmaktadır.

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametre.<br /><br /> Başvuruları aramak için ek dizinler belirtir. Daha fazla bilgi için bkz: [-lib (C# derleyici seçenekleri).](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option) |
| `AddModules` | İsteğe bağlı `String` parametre.<br /><br /> Bir veya daha fazla modülün montajın bir parçası olmasını belirtir. Daha fazla bilgi için bkz: [-addmodule (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true` [güvenli olmayan](/dotnet/csharp/language-reference/keywords/unsafe) anahtar sözcüğü kullanan kodu derlerse. Daha fazla bilgi için bkz: [-güvensiz (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | İsteğe bağlı `String` parametre.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir. |
| `BaseAddress` | İsteğe bağlı `String` parametre.<br /><br /> DLL yüklemek için tercih edilen temel adresi belirtir. Bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma süresi tarafından ayarlanır. Daha fazla bilgi için bkz: [-baseaddress (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | İsteğe bağlı `Boolean` parametre.<br /><br /> Veri türünün sınırlarını taşan tamsayı aritmetiğinin çalışma zamanında bir özel durum neden olup olmadığını belirtir. Daha fazla bilgi için bkz: [-denetlenmiş (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | İsteğe bağlı `Int32` parametre.<br /><br /> Derlemedeki tüm kaynak kod dosyaları için kullanılacak kod sayfasını belirtir. Daha fazla bilgi için bkz: [-codepage (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | İsteğe bağlı `String` parametre.<br /><br /> Hata ayıklama türünü belirtir. `DebugType`olabilir `full` veya `pdbonly`. Varsayılan, `full`çalışan bir programa bir hata ayıklama nın eklenmesini sağlayan bir durumdur. Program `pdbonly` hata ayıklayıcıda başlatıldığında kaynak kodunun hata ayıklanmasını sağlar, ancak yalnızca çalışan program hata ayıklayıcıya bağlı olduğunda assembler görüntüler.<br /><br /> Bu parametre parametreyi `EmitDebugInformation` geçersiz kılar.<br /><br /> Daha fazla bilgi için bkz: [-hata ayıklama (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | İsteğe bağlı `String` parametre.<br /><br /> Önişlemci sembollerini tanımlar. Daha fazla bilgi için bkz: [-define (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`yalnızca ortak anahtarı derlemeye yerleştirmek istediğinizi belirtirse. Eğer, `false`tam olarak imzalanmış bir derleme istediğinizi belirtirse<br /><br /> Bu parametre, parametre `KeyFile` ile `KeyContainer` kullanılmadığı sürece hiçbir etkisi yoktur.<br /><br /> Daha fazla bilgi için bkz: [-delaysign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | İsteğe bağlı `Boolean` parametre.<br/><br/> Eğer, `true`derleyicinin, girişler aynıysa, ikili içeriği derlemeler arasında aynı olan bir derlemeyi çıktısına neden olur.<br/><br/>Daha fazla bilgi için bkz: [-deterministic (C# Derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | İsteğe bağlı `String` parametre.<br /><br /> Devre dışı alınacak uyarıların listesini belirtir. Daha fazla bilgi için bkz: [-nowarn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | İsteğe bağlı `String` parametre.<br /><br /> Belge açıklamalarını bir XML dosyasına işler. Daha fazla bilgi için bkz: [-doc (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametre.<br /><br /> Görev `true`hata ayıklama bilgilerini oluşturur ve bir program veritabanı (.pdb) dosyasına yerleştirir. Eğer `false`, görev hata ayıklama bilgisi yayar. `false` varsayılan değerdir. Daha fazla bilgi için bkz: [-hata ayıklama (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | İsteğe bağlı `String` parametre.<br /><br /> C# iç hatasını Microsoft'a bildirmek için kullanışlı bir yol sağlar. Bu parametre `prompt`, `send`veya `none`. Parametre `prompt`ayarlanmışsa, bir iç derleyici hatası oluştuğunda bir istem alırsınız. İstem, Microsoft'a elektronik olarak bir hata raporu göndermenize olanak tanır. Parametre `send`ayarlanmışsa, hata raporu otomatik olarak gönderilir. Parametre `none`ayarlanmışsa, hata yalnızca derleyicinin metin çıktısında bildirilir. `none` varsayılan değerdir. Daha fazla bilgi için bkz: [-errorreport (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | İsteğe bağlı `Int32` parametre.<br /><br /> Çıktı dosyasındaki bölümlerin boyutunu belirtir. Daha fazla bilgi için bkz: [-filealign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametre.<br /><br /> If, `true`derleyici çıkışında dosyaya mutlak yolu belirtir. Eğer, `false`dosyanın adını belirtir. `false` varsayılan değerdir. Daha fazla bilgi için bkz: [-fullpaths (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtar kapsayıcısının adını belirtir. Daha fazla bilgi için bkz: [-keycontainer (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz: [-keyfile (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | İsteğe bağlı `String` parametre.<br /><br /> Kullanılacak dilin sürümünü belirtir. Daha fazla bilgi için bkz: [-langversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıktı dosyasındaki bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıktı dosyasına yerleştirilmez.<br /><br /> Bu parametreye geçirilen öğeler, isteğe `LogicalName` `Access`bağlı meta veri girişlerine adlandırılmış olabilir ve . `LogicalName`anahtarın `identifier` parametresine karşılık gelir `Access` ve parametreye `accessibility-modifier` karşılık gelir. `/linkresource` Daha fazla bilgi için [bkz: -linkresource (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | İsteğe bağlı `String` parametre.<br /><br /> `Main` Yöntemin konumunu belirtir. Daha fazla bilgi için bkz: [-main (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametre.<br /><br /> Bu modülün parçası olacağını derlemenin adını belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, derleyicic.rsp dosyası *csc.rsp* ile derlemek için değil söyler. Daha fazla bilgi için bkz: [-noconfig (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`derleyici banner bilgilerinin görüntülenmesini bastırır. Daha fazla bilgi için bkz: [-nologo (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, tüm Sistem ad alanını tanımlayan *mscorlib.dll'nin*içe aktarını engeller. Kendi Sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu parametreyi kullanın. Daha fazla bilgi için bkz: [-nostdlib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsayılan `true`Win32 bildirimini içermiyorsanız. |
| `Optimize` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`optimizasyonları sağlar. Eğer, `false`optimizasyonları devre dışı kılabilir. Daha fazla bilgi için bkz: [-optimize (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | İsteğe bağlı `String` çıktı parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Daha fazla bilgi için bkz: [-out (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı başvurusu derleme dosyasının adını belirtir. Daha fazla bilgi için bkz: [-refout (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | İsteğe bağlı `String` parametre.<br /><br /> Hata ayıklama bilgileri dosya adını belirtir. Varsayılan ad, *.pdb* uzantılı çıktı dosyası adıdır. |
| `Platform` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyası tarafından hedeflenecek işlemci platformlarını belirtir. Bu parametre `x86`, `x64`veya `anycpu`. `anycpu` varsayılan değerdir. Daha fazla bilgi için bkz: [-platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Görevin, belirtilen maddelerden geçerli projeye ortak tür bilgilerini almasına neden olur. Daha fazla bilgi için bkz: [-reference (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Bir MSBuild dosyasında, meta verileri `Aliases` özgün "Başvuru" öğesine ekleyerek C# başvuru takma adını belirtebilirsiniz. Örneğin, aşağıdaki Csc komut satırında "LS1" takma adını ayarlamak için:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> kullanacağınız:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir .NET Framework kaynağını çıktı dosyasına yerle bir eder.<br /><br /> Bu parametreye geçirilen öğeler, isteğe `LogicalName` `Access`bağlı meta veri girişlerine adlandırılmış olabilir ve . `LogicalName`anahtarın `identifier` parametresine karşılık gelir `Access` ve parametreye `accessibility-modifier` karşılık gelir. `/resource` Daha fazla bilgi için bkz: [-kaynak (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | İsteğe bağlı `String` parametre.<br /><br /> Bu görev için komutlar içeren yanıt dosyasını belirtir. Daha fazla bilgi için @ [(Yanıt dosyalarını belirt)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir veya daha fazla C# kaynak dosyabelirtir. |
| `TargetType` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir `library`konsol uygulaması oluşturan bir `exe`kod kitaplığı oluşturan `module`, bir modül oluşturan veya `winexe`bir Windows programı oluşturan bir değere sahip olabilir. Varsayılan değer: `library`. Daha fazla bilgi için bkz: [-hedef (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`tüm uyarıları hata olarak ele alırsa. Daha fazla bilgi için bkz: [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa, işlem içi derleyici nesnesini kullanma görevini bildirir. Sadece Visual Studio tarafından kullanılır. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametre.<br /><br /> UTF-8 kodlamasını kullanarak derleyici çıktısını kaydeder. Daha fazla bilgi için bkz: [-utf8output (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | İsteğe bağlı `Int32` parametre.<br /><br /> Derleyicinin görüntülenmesi için uyarı düzeyini belirtir. Daha fazla bilgi için bkz: [-warn (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak ele almak için bir uyarı listesi belirtir. Daha fazla bilgi için bkz: [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre parametreyi `TreatWarningsAsErrors` geçersiz kılar. |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametre.<br /><br /> Hata olarak kabul edilmeyen uyarıların listesini belirtir. Daha fazla bilgi için bkz: [-warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre yalnızca parametre `TreatWarningsAsErrors` `true`' ye ayarlanırsa kullanışlıdır. |
| `Win32Icon` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına **Dosya Gezgini'nde**istenen görünümü veren bir *.ico* dosyasını derlemeye ekler. Daha fazla bilgi için [-win32icon (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)bakın. |
| `Win32Manifest` | İsteğe bağlı `String` parametre.<br /><br /> Win32 manifestosunun dahil edilmesi gerektiğini belirtir. |
| `Win32Resource` | İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına win32 kaynağı (*.res*) dosyası ekler. Daha fazla bilgi için [-win32res (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option)bakın. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev `Microsoft.Build.Tasks.ManagedCompiler` sınıftan devralınan <xref:Microsoft.Build.Tasks.ToolTaskExtension> ve <xref:Microsoft.Build.Utilities.ToolTask> kendisinden devralan parametreleri sınıftan devralır. Bu ek parametrelerin ve açıklamalarının listesi için [ToolTaskExtension taban sınıfına](../msbuild/tooltaskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Csc` `Compile` madde koleksiyonundaki kaynak dosyalardan yürütülebilir bir işlem derlemek için görevi kullanır.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
