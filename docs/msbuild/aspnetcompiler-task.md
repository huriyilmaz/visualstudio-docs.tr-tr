---
title: ASP.NET uygulamalarını önceden derlemek için AspNetCompiler görevi kullanma | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6535dbec7c09f0888d0fb29a2e6b801632da22f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593466"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler görevi
`AspNetCompiler` görev, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamaları önceden derlemeye yönelik bir yardımcı program olan *aspnet_compiler. exe*' yi sarmalanmış.

## <a name="task-parameters"></a>Görev parametreleri
Aşağıdaki tabloda `AspNetCompiler` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`ise, tanımlayıcı ad derlemesi kısmen güvenilen çağıranlara izin verir.|
|`Clean`|İsteğe bağlı `Boolean` parametresi<br /><br /> Bu parametre `true`ise, önceden derlenmiş uygulama temiz oluşturulur. Önceden derlenen tüm bileşenler yeniden derlenir. Varsayılan değer `false` şeklindedir. Bu parametre *aspnet_compiler. exe*üzerindeki **-c** anahtarına karşılık gelir.|
|`Debug`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, hata ayıklama bilgileri (. PDB dosyası) derleme sırasında yayılır. Varsayılan değer `false` şeklindedir. Bu parametre *aspnet_compiler. exe*üzerindeki **-d** anahtarına karşılık gelir.|
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`ise, derleme oluşturulduğunda tamamen imzalanmaz.|
|`FixedNames`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, derlenmiş derlemelere sabit adlar verilir.|
|`Force`|İsteğe bağlı `Boolean` parametresi<br /><br /> Bu parametre `true`, zaten varsa, görev hedef dizinin üzerine yazar. Mevcut içerikler kaybedilir. Varsayılan değer `false` şeklindedir. Bu parametre *aspnet_compiler. exe*üzerindeki **-f** anahtarına karşılık gelir.|
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Bir tanımlayıcı ad anahtar kapsayıcısı belirtir.|
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Tanımlayıcı ad anahtar dosyasının fiziksel yolunu belirtir..|
|`MetabasePath`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın tam IIS metatabanı yolunu belirtir. Bu parametre `VirtualPath` veya `PhysicalPath` parametreleriyle birleştirilemez. Bu parametre *aspnet_compiler. exe*üzerindeki **-e** anahtarına karşılık gelir.|
|`PhysicalPath`|İsteğe bağlı `String` parametresi.<br /><br /> Derlenecek uygulamanın fiziksel yolunu belirtir. Bu parametre eksikse, IIS metatabanı uygulamayı bulmak için kullanılır. Bu parametre *aspnet_compiler. exe*üzerindeki **-p** anahtarına karşılık gelir.|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametresi.<br /><br /> *Aspnet_compiler. exe* ' nin .NET Framework sürümünün kullanılması gerektiğini belirten Targetframeworkbilinen adını belirtir. Yalnızca .NET Framework bilinen adları kabul eder.|
|`TargetPath`|İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın derlendiği fiziksel yolu belirtir. Belirtilmemişse, uygulama yerinde önceden derlenmiş olur.|
|`Updateable`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Bu parametre `true`, önceden derlenmiş uygulama güncelleştirilebilir olur.  Varsayılan değer `false` şeklindedir. Bu parametre *aspnet_compiler. exe*üzerindeki **-u** anahtarına karşılık gelir.|
|`VirtualPath`|İsteğe bağlı `String` parametresi.<br /><br /> Derlenecek uygulamanın sanal yolu. `PhysicalPath` belirtilmişse, uygulamayı bulmak için fiziksel yol kullanılır. Aksi takdirde, IIS metatabanı kullanılır ve uygulamanın varsayılan sitede olduğu varsayılır. Bu parametre *aspnet_compiler. exe*üzerindeki **-v** anahtarına karşılık gelir.|

## <a name="remarks"></a>Açıklamalar
Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.ToolTask> sınıfından devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki kod örneği, bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasını önceden derlemek için `AspNetCompiler` görevini kullanır.

```xml
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

## <a name="see-also"></a>Ayrıca bkz.
* [Görevler](../msbuild/msbuild-tasks.md)
* [Görev başvurusu](../msbuild/msbuild-task-reference.md)
