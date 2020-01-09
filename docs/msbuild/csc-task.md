---
title: Csc görevi | Microsoft Docs
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
ms.openlocfilehash: 7443ba29a743f4936ae104d9d0bb556fae3c4e2d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595390"
---
# <a name="csc-task"></a>Csc görevi
*CSC. exe*' yi sarmalayan ve yürütülebilir dosyalar ( *. exe* dosyaları), dinamik bağlantı kitaplıkları ( *. dll* dosyaları) veya kod modülleri ( *. netmodule* dosyaları) oluşturur. *CSC. exe*hakkında daha fazla bilgi için bkz [ C# . derleyici seçenekleri](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametreler
Aşağıdaki tabloda `Csc` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|------------------------------| - |
| `AdditionalLibPaths` | İsteğe bağlı `String[]` parametresi.<br /><br /> Başvuruların aranacağı ek dizinleri belirtir. Daha fazla bilgi için bkz. [-libC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | İsteğe bağlı `String` parametresi.<br /><br /> Derlemenin parçası olacak bir veya daha fazla modül belirtir. Daha fazla bilgi için bkz. [-addmoduleC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) anahtar sözcüğünü kullanan kodu derler. Daha fazla bilgi için bkz. [-unsafeC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | İsteğe bağlı `String` parametresi.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir. |
| `BaseAddress` | İsteğe bağlı `String` parametresi.<br /><br /> DLL 'nin yükleneceği tercih edilen temel adresi belirtir. Bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma zamanı tarafından ayarlanır. Daha fazla bilgi için bkz. [-BaseAddressC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Veri türünün sınırlarını aşan tamsayı aritmetiğinin çalışma zamanında bir özel duruma neden olup olmayacağını belirtir. Daha fazla bilgi için bkz. [-CheckedC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | İsteğe bağlı `Int32` parametresi.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Daha fazla bilgi için bkz. [-CodePageC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | İsteğe bağlı `String` parametresi.<br /><br /> Hata ayıklama türünü belirtir. `DebugType` `full` veya `pdbonly`olabilir. Varsayılan değer, bir hata ayıklayıcının çalışan bir programa eklenmesini sağlayan `full`. `pdbonly` belirtmek, program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamayı sağlar, ancak çalışan program hata ayıklayıcıya eklendiğinde yalnızca assembler 'yi görüntüler.<br /><br /> Bu parametre `EmitDebugInformation` parametresini geçersiz kılar.<br /><br /> Daha fazla bilgi için bkz. [-DebugC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | İsteğe bağlı `String` parametresi.<br /><br /> Önişlemci sembolleri tanımlar. Daha fazla bilgi için bkz. [-defineC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, yalnızca ortak anahtarı derlemeye koymak istediğinizi belirtir. `false`, tam olarak imzalanan bir derleme istediğinizi belirtir<br /><br /> `KeyFile` veya `KeyContainer` parametresiyle kullanılmamışsa bu parametrenin hiçbir etkisi yoktur.<br /><br /> Daha fazla bilgi için bkz. [-delaysignC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | İsteğe bağlı `Boolean` parametresi.<br/><br/> `true`, derleyicinin özdeş olması halinde ikili içeriği derlemeler genelinde özdeş olan bir derlemeyi çıkışına neden olur.<br/><br/>Daha fazla bilgi için bkz. [-belirleyiciC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | İsteğe bağlı `String` parametresi.<br /><br /> Devre dışı bırakılacak uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-nowarnC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | İsteğe bağlı `String` parametresi.<br /><br /> Belge açıklamalarını bir XML dosyasına işler. Daha fazla bilgi için bkz. [-docC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev hata ayıklama bilgilerini oluşturur ve bir program veritabanı (. pdb) dosyasına koyar. `false`, görev hata ayıklama bilgilerini yayar. Varsayılan değer `false`. Daha fazla bilgi için bkz. [-DebugC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | İsteğe bağlı `String` parametresi.<br /><br /> , Microsoft 'a bir C# iç hata raporlamak için kullanışlı bir yol sağlar. Bu parametre `prompt`, `send`veya `none`değerine sahip olabilir. Parametre `prompt`olarak ayarlandıysa, iç derleyici hatası oluştuğunda bir istem alırsınız. İstem bir hata raporunu Microsoft 'a elektronik olarak göndermenizi sağlar. Parametre `send`olarak ayarlandıysa, otomatik olarak bir hata raporu gönderilir. Parametre `none`olarak ayarlandıysa, hata yalnızca derleyicinin metin çıktısında raporlanır. Varsayılan değer `none`. Daha fazla bilgi için bkz. [-errorreportC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | İsteğe bağlı `Int32` parametresi.<br /><br /> Çıkış dosyasındaki bölümlerin boyutunu belirtir. Daha fazla bilgi için bkz. [-filealignC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, derleyici çıkışında dosyanın mutlak yolunu belirtir. `false`, dosyanın adını belirtir. Varsayılan değer `false`. Daha fazla bilgi için bkz. [-fullpathsC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Daha fazla bilgi için bkz. [-keycontainerC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | İsteğe bağlı `String` parametresi.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [-keyfileC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Kullanılacak dilin sürümünü belirtir. Daha fazla bilgi için bkz. [-langversionC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez.<br /><br /> Bu parametreye geçirilen öğeler `LogicalName` ve `Access`adlı isteğe bağlı meta veri girişlerine sahip olabilir. `LogicalName`, `/linkresource` anahtarın `identifier` parametresine karşılık gelir ve `Access` `accessibility-modifier` parametresine karşılık gelir. Daha fazla bilgi için bkz. [-linkresourceC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | İsteğe bağlı `String` parametresi.<br /><br /> `Main` yönteminin konumunu belirtir. Daha fazla bilgi için bkz. [-MainC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Bu modülün bir parçası olacağı derlemenin adını belirtir. |
| `NoConfig` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, derleyiciye *CSC. rsp* dosyası ile derlenmeyeceğini söyler. Daha fazla bilgi için bkz. [-noconfigC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, derleyici başlık bilgilerinin görüntülenmesini önler. Daha fazla bilgi için bkz. [-nologoC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, tüm sistem ad alanını tanımlayan *mscorlib. dll*' nin içeri aktarımını önler. Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu parametreyi kullanın. Daha fazla bilgi için bkz. [-nostdlibC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, varsayılan Win32 bildirimini eklemeyin. |
| `Optimize` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, iyileştirmeleri etkinleştirilir. `false`, iyileştirmeleri devre dışı bırakır. Daha fazla bilgi için bkz. [-optimizeC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Daha fazla bilgi için bkz. [-OutC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış başvurusu derleme dosyasının adını belirtir. Daha fazla bilgi için bkz. [-refoutC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | İsteğe bağlı `String` parametresi.<br /><br /> Hata ayıklama bilgi dosyası adını belirtir. Varsayılan ad, *. pdb* uzantılı çıkış dosyası adıdır. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Çıkış dosyası tarafından hedeflenen işlemci platformunu belirtir. Bu parametre `x86`, `x64`veya `anycpu`değerine sahip olabilir. Varsayılan değer `anycpu`. Daha fazla bilgi için bkz. [-PlatformC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Görevin, belirtilen öğelerden ortak tür bilgilerini geçerli projeye almasına neden olur. Daha fazla bilgi için bkz. [-ReferenceC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Özgün "başvuru" öğesine meta veri `Aliases` ekleyerek bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dosyasında [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] başvuru diğer adı belirtebilirsiniz. Örneğin, aşağıdaki CSC komut satırında "LS1" diğer adını ayarlamak için:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Şunu kullanabilirsiniz:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir .NET Framework kaynağını çıkış dosyasına katıştırır.<br /><br /> Bu parametreye geçirilen öğeler `LogicalName` ve `Access`adlı isteğe bağlı meta veri girişlerine sahip olabilir. `LogicalName`, `/resource` anahtarın `identifier` parametresine karşılık gelir ve `Access` `accessibility-modifier` parametresine karşılık gelir. Daha fazla bilgi için bkz. [-ResourceC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | İsteğe bağlı `String` parametresi.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir veya daha fazla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kaynak dosyasını belirtir. |
| `TargetType` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre bir `library`değerine sahip olabilir, bu, bir konsol uygulaması oluşturan `exe`, bir modül oluşturan `module`, bir Windows programı oluşturan `winexe`. Varsayılan değer `library` şeklindedir. Daha fazla bilgi için bkz. [-targetC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, tüm uyarıları hata olarak değerlendirir. Daha fazla bilgi için bkz. [-warnaserrorC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Görev, varsa, işlem içi derleyici nesnesini kullanmasını söyler. Yalnızca [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tarafından kullanılır. |
| `Utf8Output` | İsteğe bağlı `Boolean` parametresi.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Daha fazla bilgi için bkz. [-utf8outputC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | İsteğe bağlı `Int32` parametresi.<br /><br /> Derleyicinin görüntüleyeceği uyarı düzeyini belirtir. Daha fazla bilgi için bkz. [-WarnC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirmek için uyarıların listesini belirtir. Daha fazla bilgi için bkz. [-warnaserrorC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre `TreatWarningsAsErrors` parametresini geçersiz kılar. |
| `WarningsNotAsErrors` | İsteğe bağlı `String` parametresi.<br /><br /> Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Daha fazla bilgi için bkz. [-warnaserrorC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Bu parametre yalnızca `TreatWarningsAsErrors` parametresi `true`olarak ayarlandıysa faydalıdır. |
| `Win32Icon` | İsteğe bağlı `String` parametresi.<br /><br /> **Dosya Gezgini**'nde, çıktı dosyasına istenen görünümü sağlayan bir *. ico* dosyasını derlemeye ekler. Daha fazla bilgi için bkz. [-win32iconC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | İsteğe bağlı `String` parametresi.<br /><br /> Dahil edilecek Win32 bildirimini belirtir. |
| `Win32Resource` | İsteğe bağlı `String` parametresi.<br /><br /> Çıktı dosyasına bir Win32 kaynağı ( *. res*) dosyası ekler. Daha fazla bilgi için bkz. [-win32resC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Açıklamalar
Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.ToolTask> sınıfından devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfından devralan `Microsoft.Build.Tasks.ManagedCompiler` sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki örnek, `Compile` öğesi koleksiyonundaki kaynak dosyalardan bir yürütülebilir dosya derlemek için `Csc` görevini kullanır.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
