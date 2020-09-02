---
title: Vbc görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6edc8b246055dcd8efdb32f4118f81a535635d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683823"
---
# <a name="vbc-task"></a>Vbc Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yürütülebilir dosyalar (. exe), dinamik bağlantı kitaplıkları (. dll) veya kod modülleri (. netmodule) üreten vbc.exe kaydırır. vbc.exe hakkında daha fazla bilgi için bkz. [Visual Basic komut satırı derleyicisi](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `Vbc` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AdditionalLibPaths`|İsteğe bağlı `String[]` parametre.<br /><br /> Başvurular özniteliğinde belirtilen derlemelerin aranacağı ek klasörleri belirtir.|  
|`AddModules`|İsteğe bağlı `String[]` parametre.<br /><br /> Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur. Bu parametre vbc.exe derleyicisinin [/addmodule](https://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) anahtarına karşılık gelir.|  
|`BaseAddress`|İsteğe bağlı `String` parametre.<br /><br /> DLL 'nin temel adresini belirtir. Bu parametre vbc.exe derleyicisinin [/BaseAddress](https://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) anahtarına karşılık gelir.|  
|`CodePage`|İsteğe bağlı `Int32` parametre.<br /><br /> Derlemedeki tüm kaynak kodu dosyaları için kullanılacak kod sayfasını belirtir. Bu parametre vbc.exe derleyicisinin [/CodePage](https://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) anahtarına karşılık gelir.|  
|`DebugType`|İsteğe bağlı `String[]` parametre.<br /><br /> Derleyicinin hata ayıklama bilgileri oluşturmasına neden olur. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Varsayılan değer `full` , çalışan programa hata ayıklayıcı iliştirmeyi sağlar. Bir değeri, `pdbonly` program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde derleme dili kodunu görüntüler. Daha fazla bilgi için bkz. [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|İsteğe bağlı `String[]` parametre.<br /><br /> Koşullu derleyici sabitlerini tanımlar. Sembol/değer çiftleri noktalı virgülle ayrılır ve aşağıdaki sözdizimiyle belirtilir:<br /><br /> *symbol1* `=` *değer1* `;` *symbol2* `=` *değer2*<br /><br /> Bu parametre vbc.exe derleyicisinin [/define](https://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) anahtarına karşılık gelir.|  
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev ortak anahtarı derlemeye koyar. İse `false` , görev derlemeyi tamamen imzalar. Varsayılan değer `false` . Parametresi veya parametresiyle kullanılmamışsa bu parametrenin etkisi yoktur `KeyFile` `KeyContainer` . Bu parametre vbc.exe derleyicisinin [/delaysign](https://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) anahtarına karşılık gelir.|  
|`DisabledWarnings`|İsteğe bağlı `String` parametre.<br /><br /> Belirtilen uyarıları bastırır. Uyarı tanımlayıcısının sayısal bölümünü belirtmeniz yeterlidir. Birden çok uyarı noktalı virgülle ayrılır. Bu parametre vbc.exe derleyicisinin [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) anahtarına karşılık gelir.|  
|`DocumentationFile`|İsteğe bağlı `String` parametre.<br /><br /> Belge açıklamalarını belirtilen XML dosyasına işler. Bu parametre, özniteliğini geçersiz kılar `GenerateDocumentation` . Daha fazla bilgi için bkz. [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Görev hata ayıklama bilgilerini oluşturur ve bir. pdb dosyasına koyar. Daha fazla bilgi için bkz. [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|İsteğe bağlı `String` parametre.<br /><br /> Görevin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> `prompt`Belirtilmişse ve bir iç derleyici hatası oluşursa, kullanıcıdan hata verilerini Microsoft 'a göndermek için bir seçenek istenir.<br /><br /> `send`Belirtilmişse ve bir iç derleyici hatası oluşursa, görev hata verilerini Microsoft 'a gönderir.<br /><br /> Varsayılan değer `none` , hataları yalnızca metin çıktısında raporlayan.<br /><br /> Bu parametre vbc.exe derleyicisinin [/errorreport](https://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) anahtarına karşılık gelir.|  
|`FileAlignment`|İsteğe bağlı `Int32` parametre.<br /><br /> Çıktı dosyasının bölümlerinin hizalanın bayt cinsinden sayısını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Bu parametre vbc.exe derleyicisinin [/filealign](https://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) anahtarına karşılık gelir.|  
|`GenerateDocumentation`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , belge bilgilerini oluşturur ve görevin oluşturduğu yürütülebilir dosyanın veya kitaplığın adıyla BIR XML dosyasına koyar. Daha fazla bilgi için bkz. [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Belirtilen öğe koleksiyonlarından ad alanlarını içeri aktarır. Bu parametre vbc.exe derleyicisinin [/Imports](https://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) anahtarına karşılık gelir.|  
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarı kapsayıcısının adını belirtir. Bu parametre vbc.exe derleyicisinin [/keycontainer](https://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) anahtarına sahiptir.|  
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Şifreleme anahtarını içeren dosya adını belirtir. Daha fazla bilgi için bkz. [/keyfile](https://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|İsteğe bağlı [dize] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->parametresinin.<br /><br /> "9" veya "10" dil sürümünü belirtir.|  
|`LinkResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez. Bu parametre vbc.exe derleyicisinin [/linkresource](https://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) anahtarına karşılık gelir.|  
|`MainEntryPoint`|İsteğe bağlı `String` parametre.<br /><br /> Yordamı içeren sınıfı veya modülü belirtir `Sub Main` . Bu parametre vbc.exe derleyicisinin [/Main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) anahtarına sahiptir.|  
|`ModuleAssemblyName`|İsteğe bağlı `String` parametre.<br /><br /> Bu modülün bir parçası olduğu derlemeyi belirtir.|  
|`NoConfig`|İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyicinin Vbc. rsp dosyasını kullanması gerektiğini belirtir. Bu parametre vbc.exe derleyicisinin [/noconfig](https://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) parametresine karşılık gelir.|  
|`NoLogo`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici başlık bilgilerinin görüntülenmesini önler. Bu parametre vbc.exe derleyicisinin [/nologo](https://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) anahtarına karşılık gelir.|  
|`NoStandardLib`|İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyicinin standart kitaplıklara Başvurmamasını sağlar. Bu parametre vbc.exe derleyicisinin [/nostdlib](https://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) anahtarına karşılık gelir.|  
|`NoVBRuntimeReference`|İsteğe bağlı `Boolean` parametre.<br /><br /> Yalnızca iç kullanım. True ise Microsoft.VisualBasic.dll otomatik başvuruyu önler..|  
|`NoWarnings`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , görev tüm uyarıları bastırır. Daha fazla bilgi için bkz. [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , derleyici iyileştirmelerine izin vermez. Bu parametre vbc.exe derleyicisinin [/optimize](https://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) anahtarına karşılık gelir.|  
|`OptionCompare`|İsteğe bağlı `String` parametre.<br /><br /> Dize karşılaştırmalarının nasıl yapılacağını belirtir. Bu parametre aşağıdaki değerlere sahip olabilir:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Değer, `binary` görevin ikili dize karşılaştırmaları kullandığını belirtir. Değer, `text` görevin metin dizesi karşılaştırmaları kullandığını belirtir. Bu parametrenin varsayılan değeri `binary` . Bu parametre vbc.exe derleyicisinin [/OptionCompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) anahtarına karşılık gelir.|  
|`OptionExplicit`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , değişkenlerin açık bildirimi gereklidir. Bu parametre, vbc.exe derleyicisinin [/OptionExplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) anahtarına karşılık gelir.|  
|`OptionInfer`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , değişkenlerin tür çıkarımını izin verir.|  
|`OptionStrict`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev, örtük tür dönüştürmeleri kısıtlamak için katı tür semantiğini zorlar. Bu parametre vbc.exe derleyicisinin [/OptionStrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) anahtarına karşılık gelir.|  
|`OptionStrictType`|İsteğe bağlı `String` parametre.<br /><br /> Hangi katı tür semantiğinin uyarı ürettiğini belirtir. Şu anda yalnızca "Custom" desteklenir. Bu parametre vbc.exe derleyicisinin [/OptionStrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) anahtarına karşılık gelir.|  
|`OutputAssembly`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Çıktı dosyasının adını belirtir. Bu parametre vbc.exe derleyicisinin [/Out](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) anahtarına karşılık gelir.|  
|`Platform`|İsteğe bağlı `String` parametre.<br /><br /> Çıkış dosyası tarafından hedeflenen işlemci platformunu belirtir. Bu parametre,,, veya değerine sahip olabilir `x86` `x64` `Itanium` `anycpu` . `anycpu` varsayılan değerdir. Bu parametre vbc.exe derleyicisinin [/Platform](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) anahtarına karşılık gelir.|  
|`References`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Görevin, belirtilen öğelerden ortak tür bilgilerini geçerli projeye almasına neden olur. Bu parametre vbc.exe derleyicisinin [/Reference](https://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) anahtarına karşılık gelir.|  
|`RemoveIntegerChecks`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , tamsayı taşma hata denetimlerini devre dışı bırakır. Varsayılan değer: `false`. Bu parametre vbc.exe derleyicisinin [/removeintchecks](https://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) anahtarına karşılık gelir.|  
|`Resources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir .NET Framework kaynağını çıkış dosyasına katıştırır. Bu parametre vbc.exe derleyicisinin [/Resource](https://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) anahtarına karşılık gelir.|  
|`ResponseFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bu görev için komutları içeren yanıt dosyasını belirtir. Bu parametre, vbc.exe derleyicisinin [@ (yanıt dosyasını belirt)](https://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) seçeneğine karşılık gelir.|  
|`RootNamespace`|İsteğe bağlı `String` parametre.<br /><br /> Tüm tür bildirimlerinin kök ad alanını belirtir. Bu parametre vbc.exe derleyicisinin [/RootNamespace](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) anahtarına karşılık gelir.|  
|`SdkPath`|İsteğe bağlı `String` parametre.<br /><br /> mscorlib.dll ve microsoft.visualbasic.dll konumunu belirtir. Bu parametre vbc.exe derleyicisinin [/SdkPath](https://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) anahtarına karşılık gelir.|  
|`Sources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bir veya daha fazla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kaynak dosyasını belirtir.|  
|`TargetCompactFramework`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse, `true` görev öğesini hedefler [!INCLUDE[Compact](../includes/compact-md.md)] . Bu anahtar vbc.exe derleyicisinin [/netcf](https://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) anahtarına karşılık gelir.|  
|`TargetType`|İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasının dosya biçimini belirtir. Bu parametre, bir, bir `library` `exe` `module` Windows programı oluşturan veya bir modül oluşturan bir konsol uygulaması oluşturan bir ' ' değeri olabilir `winexe` . `library` varsayılan değerdir. Bu parametre vbc.exe derleyicisinin [/target](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) anahtarına karşılık gelir.|  
|`Timeout`|İsteğe bağlı `Int32` parametre.<br /><br /> Görev yürütülebilir dosyasının sonlandırılacağı süre (milisaniye cinsinden) sayısını belirtir. Varsayılan değer `Int.MaxValue` , zaman aşımı süresi olmadığını gösterir.|  
|`ToolPath`|İsteğe bağlı `String` parametre.<br /><br /> Görevin temel alınan yürütülebilir dosyayı (vbc.exe) yükleyecek konumu belirtir. Bu parametre belirtilmezse, görev, çalıştıran çerçevenin sürümüne karşılık gelen SDK yükleme yolunu kullanır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|`TreatWarningsAsErrors`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , tüm uyarılar hata olarak değerlendirilir. Daha fazla bilgi için bkz. [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|İsteğe bağlı `Boolean` parametre.<br /><br /> Görev, varsa, işlem içi derleyici nesnesini kullanmasını söyler. Yalnızca tarafından kullanılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|`Utf8Output`|İsteğe bağlı `Boolean` parametre.<br /><br /> Derleyici çıkışını UTF-8 kodlaması kullanarak günlüğe kaydeder. Bu parametre vbc.exe derleyicisinin [/utf8output](https://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) anahtarına karşılık gelir.|  
|`Verbosity`|İsteğe bağlı `String` parametre.<br /><br /> Derleyicinin çıkışının ayrıntı düzeyini belirtir. Ayrıntı düzeyi `Quiet` , `Normal` (varsayılan) veya olabilir `Verbose` .|  
|`WarningsAsErrors`|İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirmek için uyarıların listesini belirtir. Daha fazla bilgi için bkz. [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Bu parametre, parametresini geçersiz kılar `TreatWarningsAsErrors` .|  
|`WarningsNotAsErrors`|İsteğe bağlı `String` parametre.<br /><br /> Hata olarak değerlendirilmediğini belirten uyarıların bir listesini belirtir. Daha fazla bilgi için bkz. [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Bu parametre yalnızca `TreatWarningsAsErrors` parametresi olarak ayarlandıysa faydalıdır `true` .|  
|`Win32Icon`|İsteğe bağlı `String` parametre.<br /><br /> Dosya Gezgini 'nde, çıktı dosyasına istenen görünümü sağlayan bir. ico dosyasını derlemeye ekler. Bu parametre vbc.exe derleyicisinin [/Win32Icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) anahtarına karşılık gelir.|  
|`Win32Resources`|İsteğe bağlı `String` parametre.<br /><br /> Çıktı dosyasına bir Win32 kaynağı (. res) dosyası ekler. Bu parametre vbc.exe derleyicisinin [/Win32Resource](https://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) anahtarına karşılık gelir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir projeyi derler [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
