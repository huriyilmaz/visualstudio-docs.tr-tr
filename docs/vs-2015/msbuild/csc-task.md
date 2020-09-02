---
title: Csc görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0dd27fe64982e77872e37ec01dbdb71a0a141ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694097"
---
# <a name="csc-task"></a>Csc Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CSC.exe sarmalanmış ve yürütülebilir dosyalar (. exe dosyaları), dinamik bağlantı kitaplıkları (. dll dosyaları) veya kod modülleri (. netmodule dosyaları) oluşturur. CSC.exe hakkında daha fazla bilgi için bkz. [C# derleyici seçenekleri](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `Csc` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalLibPaths`|İsteğe bağlı `String[]` parametre.<br /><br /> Başvuruların aranacağı ek dizinleri belirtir. Daha fazla bilgi için bkz. [/lib (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|İsteğe bağlı `String` parametre.<br /><br /> Derlemenin parçası olacak bir veya daha fazla modül belirtir. Daha fazla bilgi için bkz. [/addmodule (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) anahtar sözcüğünü kullanan kodu derler. Daha fazla bilgi için bkz. [/unsafe (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|İsteğe bağlı `String` parametre.<br /><br /> Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyasını belirtir.|  
|`BaseAddress`|İsteğe bağlı `String` parametre.<br /><br /> DLL 'nin yükleneceği tercih edilen temel adresi belirtir. Bir DLL için varsayılan temel adres, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı tarafından ayarlanır. Daha fazla bilgi için bkz. [/BaseAddress (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|İsteğe bağlı `Boolean` parametre.<br /><br /> Veri türünün sınırlarını aşan tamsayı aritmetiğinin çalışma zamanında bir özel duruma neden olup olmayacağını belirtir. Daha fazla bilgi için bkz. [/checked (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|İsteğe bağlı `Int32` parametre.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Daha fazla bilgi için bkz. [/CodePage (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|İsteğe bağlı `String` parametre.<br /><br /> Hata ayıklama türünü belirtir. `DebugType` veya olabilir `full` `pdbonly` . Varsayılan değer `full` , bir hata ayıklayıcının çalışan bir programa eklenmesini sağlar. Belirleme, `pdbonly` program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamayı sağlar, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde assembler 'yi görüntüler.<br /><br /> Bu parametre, parametresini geçersiz kılar `EmitDebugInformation` .<br /><br /> Daha fazla bilgi için bkz. [/Debug (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|İsteğe bağlı `String` parametre.<br /><br /> Önişlemci sembolleri tanımlar. Daha fazla bilgi için bkz. [/define (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , tam olarak imzalanan bir derleme istediğinizi belirtir. `false`Yalnızca ortak anahtarı derlemeye yerleştirmek istediğinizi belirtir.<br /><br /> Ya da parametresiyle kullanılmamışsa, bu parametrenin hiçbir etkisi `KeyFile` yoktur `KeyContainer` .<br /><br /> Daha fazla bilgi için bkz. [/delaysign (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|İsteğe bağlı `String` parametre.<br /><br /> Devre dışı bırakılacak uyarıların listesini belirtir. Daha fazla bilgi için bkz. [/nowarn (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|İsteğe bağlı `String` parametre.<br /><br /> Belge açıklamalarını bir XML dosyasına işler. Daha fazla bilgi için bkz. [/doc (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Görev hata ayıklama bilgilerini oluşturur ve bir program veritabanı (. pdb) dosyasına koyar. İse `false` , görev hata ayıklama bilgisi içermez. `false` varsayılan değerdir. Daha fazla bilgi için bkz. [/Debug (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|İsteğe bağlı `String` parametre.<br /><br /> , C# iç hatasını Microsoft 'a bildirmenin kolay bir yolunu sağlar. Bu parametre,, veya değerine sahip `prompt` olabilir `send` `none` . Parametresi olarak ayarlandıysa `prompt` , iç derleyici hatası oluştuğunda bir istem alırsınız. İstem bir hata raporunu Microsoft 'a elektronik olarak göndermenizi sağlar. Parametresi olarak ayarlandıysa `send` , bir hata raporu otomatik olarak gönderilir. Parametresi olarak ayarlandıysa `none` , hata yalnızca derleyicinin metin çıkışında raporlanır. `none` varsayılan değerdir. Daha fazla bilgi için bkz. [/errorreport (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|İsteğe bağlı `Int32` parametre.<br /><br /> Çıkış dosyasındaki bölümlerin boyutunu belirtir. Daha fazla bilgi için bkz. [/filealign (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici çıkışında dosyanın mutlak yolunu belirtir. İse `false` , dosyanın adını belirtir. `false` varsayılan değerdir. Daha fazla bilgi için bkz. [/fullpaths (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Daha fazla bilgi için bkz. [/keycontainer (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [/keyfile (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|İsteğe bağlı `String` parametre.<br /><br /> Kullanılacak dilin sürümünü belirtir. Daha fazla bilgi için bkz. [/langversion (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıkış dosyasındaki bir kaynağa bir bağlantı oluşturur [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ; kaynak dosyası çıkış dosyasına yerleştirilmez.<br /><br /> Bu parametreye geçirilen öğeler, ve adlı isteğe bağlı meta veri girişlerine sahip olabilir `LogicalName` `Access` . `LogicalName``identifier`anahtarın parametresine karşılık gelir `/linkresource` ve `Access` parametreye karşılık gelir `accessibility-modifier` . Daha fazla bilgi için bkz. [/linkresource (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|İsteğe bağlı `String` parametre.<br /><br /> Metodun konumunu belirtir `Main` . Daha fazla bilgi için bkz. [/Main (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|İsteğe bağlı `String` parametre.<br /><br /> Bu modülün bir parçası olacağı derlemenin adını belirtir.|  
|`NoConfig`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyiciye CSC. rsp dosyası ile derlenmeyeceğini söyler. Daha fazla bilgi için bkz. [/noconfig (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici başlık bilgilerinin görüntülenmesini önler. Daha fazla bilgi için bkz. [/nologo (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Tüm sistem ad alanını tanımlayan mscorlib.dll içeri aktarmayı önler. Kendi sistem ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu parametreyi kullanın. Daha fazla bilgi için bkz. [/nostdlib (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Varsayılan Win32 bildirimini eklemeyin.|  
|`Optimize`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` iyileştirmeleri etkinleştirilir. İse `false` iyileştirmeleri devre dışı bırakır. Daha fazla bilgi için bkz. [/optimize (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Daha fazla bilgi için bkz. [/Out (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|İsteğe bağlı `String` parametre.<br /><br /> Hata ayıklama bilgi dosyası adını belirtir. Varsayılan ad,. pdb uzantılı çıkış dosyası adıdır.|  
|`Platform`|İsteğe bağlı `String` parametre.<br /><br /> Çıkış dosyası tarafından hedeflenen işlemci platformunu belirtir. Bu parametre,, veya değerine sahip `x86` olabilir `x64` `anycpu` . `anycpu` varsayılan değerdir. Daha fazla bilgi için bkz. [/Platform (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Görevin, belirtilen öğelerden ortak tür bilgilerini geçerli projeye almasına neden olur. Daha fazla bilgi için bkz. [/Reference (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] `Aliases` Özgün "başvuru" öğesine meta verileri ekleyerek bir dosyada başvuru diğer adı belirtebilirsiniz. Örneğin, aşağıdaki CSC komut satırında "LS1" diğer adını ayarlamak için:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Şunu kullanabilirsiniz:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Çıktı dosyasına bir kaynak gömer.<br /><br /> Bu parametreye geçirilen öğeler, ve adlı isteğe bağlı meta veri girişlerine sahip olabilir `LogicalName` `Access` . `LogicalName``identifier`anahtarın parametresine karşılık gelir `/resource` ve `Access` parametreye karşılık gelir `accessibility-modifier` . Daha fazla bilgi için bkz. [/Resource (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|İsteğe bağlı `String` parametre.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Daha fazla bilgi için bkz. [@ (yanıt dosyası belirtme)](https://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir veya daha fazla [!INCLUDE[csprcs](../includes/csprcs-md.md)] kaynak dosyasını belirtir.|  
|`TargetType`|İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir, bir `library` `exe` `module` Windows programı oluşturan veya bir modül oluşturan bir konsol uygulaması oluşturan bir ' ' değeri olabilir `winexe` . Varsayılan değer: `library`. Daha fazla bilgi için bkz. [/target (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , tüm uyarıları hata olarak değerlendirir. Daha fazla bilgi için bkz. [/warnaserror (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|İsteğe bağlı `Boolean` parametre.<br /><br /> Görev, varsa, işlem içi derleyici nesnesini kullanmasını söyler. Yalnızca tarafından kullanılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|`Utf8Output`|İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Daha fazla bilgi için bkz. [/utf8output (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|İsteğe bağlı `Int32` parametre.<br /><br /> Derleyicinin görüntüleyeceği uyarı düzeyini belirtir. Daha fazla bilgi için bkz. [/Warn (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirmek için uyarıların listesini belirtir. Daha fazla bilgi için bkz. [/warnaserror (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Bu parametre, parametresini geçersiz kılar `TreatWarningsAsErrors` .|  
|`WarningsNotAsErrors`|İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Daha fazla bilgi için bkz. [/warnaserror (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Bu parametre yalnızca `TreatWarningsAsErrors` parametresi olarak ayarlandıysa faydalıdır `true` .|  
|`Win32Icon`|İsteğe bağlı `String` parametre.<br /><br /> Dosya Gezgini 'nde, çıktı dosyasına istenen görünümü sağlayan bir. ico dosyasını derlemeye ekler. Daha fazla bilgi için bkz. [/Win32Icon (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|İsteğe bağlı `String` parametre.<br /><br /> Dahil edilecek Win32 bildirimini belirtir.|  
|`Win32Resource`|İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına bir Win32 kaynağı (. res) dosyası ekler. Daha fazla bilgi için bkz. [/win32res (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralan sınıfından devralan sınıfından parametreleri devralır `Microsoft.Build.Tasks.ManagedCompiler` <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Csc` öğe koleksiyonundaki kaynak dosyalardan bir yürütülebilir dosya derlemek için görevini kullanır `Compile` .  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
