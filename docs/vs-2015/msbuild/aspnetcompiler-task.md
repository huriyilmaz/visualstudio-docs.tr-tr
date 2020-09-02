---
title: AspNetCompiler görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1267ddbb093f59eaa60fae0eef2d83f6b7ba2e24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187060"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`AspNetCompiler`Görev, uygulamaları önceden derlemeye yönelik bir yardımcı program olan aspnet_compiler.exe sarmalanmış [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki tablo, görevin parametrelerini açıklar `AspNetCompiler` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise, `true` tanımlayıcı ad derlemesi kısmen güvenilen çağıranlara izin verir.|  
|`Clean`|İsteğe bağlı `Boolean` parametre<br /><br /> Bu parametre ise `true` , önceden derlenmiş uygulama temiz oluşturulur. Önceden derlenen tüm bileşenler yeniden derlenir. Varsayılan değer: `false`. Bu parametre, aspnet_compiler.exe üzerindeki **-c** anahtarına karşılık gelir.|  
|`Debug`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` hata ayıklama bilgileri (. PDB dosyası) derleme sırasında yayılır. Varsayılan değer: `false`. Bu parametre, aspnet_compiler.exe üzerindeki **-d** anahtarına karşılık gelir.|  
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` , derleme oluşturulduğunda tamamen imzalanmaz.|  
|`FixedNames`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` , derlenmiş derlemelere sabit adlar verilecek.|  
|`Force`|İsteğe bağlı `Boolean` parametre<br /><br /> Bu parametre ise `true` , zaten varsa görev hedef dizinin üzerine yazar. Mevcut içerikler kaybedilir. Varsayılan değer: `false`. Bu parametre, aspnet_compiler.exe üzerindeki **-f** anahtarına karşılık gelir.|  
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Bir tanımlayıcı ad anahtar kapsayıcısı belirtir.|  
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Tanımlayıcı ad anahtar dosyasının fiziksel yolunu belirtir..|  
|`MetabasePath`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın tam IIS metatabanı yolunu belirtir. Bu parametre `VirtualPath` veya `PhysicalPath` parametreleriyle birleştirilemez. Bu parametre, aspnet_compiler.exe üzerindeki **-e** anahtarına karşılık gelir.|  
|`PhysicalPath`|İsteğe bağlı `String` parametre.<br /><br /> Derlenecek uygulamanın fiziksel yolunu belirtir. Bu parametre eksikse, IIS metatabanı uygulamayı bulmak için kullanılır. Bu parametre, aspnet_compiler.exe üzerindeki **-p** anahtarına karşılık gelir.|  
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametre.<br /><br /> aspnet_compiler.exe hangi .NET Framework sürümünün kullanılması gerektiğini belirten Targetframeworkbilinen adını belirtir. Yalnızca .NET Framework bilinen adları kabul eder.|  
|`TargetPath`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın derlendiği fiziksel yolu belirtir. Belirtilmemişse, uygulama yerinde önceden derlenmiş olur.|  
|`Updateable`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` , önceden derlenmiş uygulama güncelleştirilebilir olur.  Varsayılan değer: `false`. Bu parametre, aspnet_compiler.exe üzerindeki **-u** anahtarına karşılık gelir.|  
|`VirtualPath`|İsteğe bağlı `String` parametre.<br /><br /> Derlenecek uygulamanın sanal yolu. `PhysicalPath`Belirtilmişse, fiziksel yol, uygulamayı bulmak için kullanılır. Aksi takdirde, IIS metatabanı kullanılır ve uygulamanın varsayılan sitede olduğu varsayılır. Bu parametre, aspnet_compiler.exe üzerindeki **-v** anahtarına karşılık gelir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `AspNetCompiler` bir uygulamayı önceden derlemek için görevini kullanır [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
