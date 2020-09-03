---
title: MSBuild ayrılmış ve Iyi bilinen Özellikler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19fa9c35011e42905c1f26ed34da405be61d0aba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181085"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild Ayrılmış ve Tanınmış Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyası ve ikili dosyalar hakkında bilgi depolayan önceden tanımlanmış özellikler kümesi sağlar [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bu özellikler diğer özelliklerle aynı şekilde değerlendirilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Örneğin, özelliğini kullanmak için `MSBuildProjectFile` , yazın `$(MSBuildProjectFile)` .  
  
 MSBuild, ayrılmış ve iyi bilinen özellikleri önceden tanımlamak için aşağıdaki tablodaki değerleri kullanır. Ayrılmış Özellikler geçersiz kılınamaz, ancak aynı adlı ortam özellikleri, genel özellikler veya proje dosyasında belirtilen özellikler kullanılarak iyi bilinen özellikler geçersiz kılınabilir.  
  
## <a name="reserved-and-well-known-properties"></a>Ayrılmış ve Tanınmış Özellikler  
 Aşağıdaki tabloda [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] önceden tanımlanmış özellikler açıklanmaktadır.  
  
|Özellik|Açıklama|Ayrılmış veya Iyi bilinen|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Kullanılmakta olan ikililerin bulunduğu klasörün mutlak yolu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] (örneğin, C:\Windows\Microsoft.Net\Framework \\ *versionNumber*). Dizindeki dosyalara başvurmanız gerekirse bu özellik faydalıdır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.|Ayrılmıştır|  
|`MSBuildExtensionsPath`|.NET Framework 4 ' te tanıtılan: varsayılan değerleri ve arasında bir fark yoktur `MSBuildExtensionsPath` `MSBuildExtensionsPath32` . `MSBUILDLEGACYEXTENSIONSPATH`Önceki sürümlerde varsayılan değerinin davranışını etkinleştirmek için ortam değişkenini null olmayan bir değere ayarlayabilirsiniz `MSBuildExtensionsPath` .<br /><br /> .NET Framework 3,5 ve önceki sürümlerde varsayılan değeri, `MSBuildExtensionsPath` geçerli işlemin bit durumuna bağlı olarak \Program Files \ veya \Program Files (x86) klasörü altındaki MSBuild alt klasörünün yolunu işaret eder. Örneğin, 64 bit bir makinedeki 32 bitlik bir işlem için bu özellik, \Program Files (x86) klasörünü işaret eder. 64 bit makinede 64 bitlik bir işlem için bu özellik \Program Files klasörünü işaret eder.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.<br /><br /> Bu konum, özel hedef dosyaları yerleştirmek için kullanışlı bir yerdir. Örneğin, hedef dosyalarınız \Program Files\msbuild\myfiles\northwind.exe dizinine yüklenip daha sonra bu XML kodu kullanılarak proje dosyalarına aktarılabilir:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|İyi bilinen|  
|`MSBuildExtensionsPath32`|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]\Program Files veya \Program Files (x86) klasörü altındaki alt klasörün yolu. Bu yol her zaman bir 32 bit makinede 32-bit \Program Files klasörünü ve 64-bit bir makinede \Program Files (x86) yolunu gösterir. Ayrıca bkz `MSBuildExtensionsPath` `MSBuildExtensionsPath64` . ve.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.|İyi bilinen|  
`MSBuildExtensionsPath64`|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]\Program Files klasörü altındaki alt klasörün yolu. 64 bitlik bir makine için bu yol her zaman \Program Files klasörünü işaret eder. 32 bitlik bir makine için bu yol boştur. Ayrıca bkz `MSBuildExtensionsPath` `MSBuildExtensionsPath32` . ve.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.|İyi bilinen|  
|`MSBuildLastTaskResult`|`true` önceki görev herhangi bir hata olmadan tamamlanırsa (Uyarılar olsa bile) veya `false` önceki görevde hatalar varsa. Genellikle, bir görevde bir hata oluştuğunda, hata bu projede gerçekleşen son şeydir. Bu nedenle, bu özelliğin değeri hiçbir `false` şekilde bu senaryolar haricinde değildir:<br /><br /> - `ContinueOnError` [Task öğesi (MSBuild)](../msbuild/task-element-msbuild.md) özniteliği `WarnAndContinue` (veya `true` ) veya olarak ayarlandığında `ErrorAndContinue` .<br /><br /> -, Bir `Target` alt öğe olarak bir Ida bir [hataöğesi (MSBuild)](../msbuild/onerror-element-msbuild.md) içerir.|Ayrılmıştır|  
|`MSBuildNodeCount`|Oluşturulurken kullanılan eşzamanlı işlem sayısı üst sınırı. Bu, komut satırında **/maxcpucount** için belirttiğiniz değerdir. Değer belirtmeden **/maxcpucount** belirttiyseniz, `MSBuildNodeCount` bilgisayardaki işlemci sayısını belirtir. Daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md) ve [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Ayrılmıştır|  
|`MSBuildProgramFiles32`|32 bit program klasörünün konumu; Örneğin, `C:\Program Files (x86)` .<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.|Ayrılmıştır|  
|`MSBuildProjectDefaultTargets`|Öğesinin özniteliğinde belirtilen hedeflerin tamamı listesi `DefaultTargets` `Project` . Örneğin, aşağıdaki `Project` öğe bir özellik değerine sahip olacaktır `MSBuildDefaultTargets` `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >`|Ayrılmıştır|  
|`MSBuildProjectDirectory`|Örneğin, proje dosyasının bulunduğu dizinin mutlak yolu `C:\MyCompany\MyProduct` .<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.|Ayrılmıştır|  
|`MSBuildProjectDirectoryNoRoot`|`MSBuildProjectDirectory`Kök sürücü hariç, özelliğin değeri.<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.|Ayrılmıştır|  
|`MSBuildProjectExtension`|Proje dosyasının süresi de dahil olmak üzere dosya adı uzantısı; Örneğin,. proj.|Ayrılmıştır|  
|`MSBuildProjectFile`|Proje dosyasının dosya adı uzantısı da dahil olmak üzere dosyanın tamamı. Örneğin, MyApp. proj.|Ayrılmıştır|  
|`MSBuildProjectFullPath`|Dosya adı uzantısı da dahil olmak üzere, proje dosyasının mutlak yolu ve tam dosya adı. Örneğin, C:\mycompany\myproduct\myapp.exe.|Ayrılmıştır|  
|`MSBuildProjectName`|Dosya adı uzantısı olmadan proje dosyasının dosya adı; Örneğin, MyApp.|Ayrılmıştır|  
|`MSBuildStartupDirectory`|Olarak adlandırılan klasörün mutlak yolu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bu özelliği kullanarak, her dizinde dizin. proj dosyaları oluşturmadan bir proje ağacındaki belirli bir noktanın altındaki her şeyi oluşturabilirsiniz. Bunun yerine, burada gösterildiği gibi yalnızca bir projeniz vardır — örneğin, c:\traversal.proj.<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Ağaçta herhangi bir noktada derlemek için şunu yazın:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Bu özelliğe son ters eğik çizgiyi eklemeyin.|Ayrılmıştır|  
|`MSBuildThisFile`|Öğesinin dosya adı ve dosya uzantısı kısmı `MSBuildThisFileFullPath` .|Ayrılmıştır|  
|`MSBuildThisFileDirectory`|Öğesinin dizin bölümü `MSBuildThisFileFullPath` .<br /><br /> Yola son ters eğik çizgiyi ekleyin.|Ayrılmıştır|  
|`MSBuildThisFileDirectoryNoRoot`|`MSBuildThisFileFullPath`Kök sürücü hariç, öğesinin dizin bölümü.<br /><br /> Yola son ters eğik çizgiyi ekleyin.|Ayrılmıştır|  
|`MSBuildThisFileExtension`|Öğesinin dosya adı uzantısı kısmı `MSBuildThisFileFullPath` .|Ayrılmıştır|  
|`MSBuildThisFileFullPath`|Çalıştıran hedefi içeren projenin veya hedef dosyanın mutlak yolu.<br /><br /> İpucu: asıl proje dosyasına göre değil, hedef dosya ile ilişkili olan bir hedefler dosyasında göreli bir yol belirtebilirsiniz.|Ayrılmıştır|  
|`MSBuildThisFileName`|Dosya adı uzantısı olmadan öğesinin dosya adı kısmı `MSBuildThisFileFullPath` .|Ayrılmıştır|  
|`MSBuildToolsPath`|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Değeri ile ilişkili sürümün yükleme yolu `MSBuildToolsVersion` .<br /><br /> Yola son ters eğik çizgiyi eklemeyin.<br /><br /> Bu özellik geçersiz kılınamaz.|Ayrılmıştır|  
|`MSBuildToolsVersion`|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Projeyi derlemek için kullanılan araç takımının sürümü.<br /><br /> Note: bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] araç takımı, bir uygulama oluşturmak için kullanılan görevlerden, hedeflerin ve araçlardan oluşur. Araçlar csc.exe ve vbc.exe gibi derleyiciler içerir. Daha fazla bilgi için bkz. [araç takımı (araçları sürümü)](../msbuild/msbuild-toolset-toolsversion.md)ve [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md).|Ayrılmıştır|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md) [MSBuild özellikleri](msbuild-properties1.md)
