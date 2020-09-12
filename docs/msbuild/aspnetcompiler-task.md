---
title: ASP.NET ön derlemek için AspNetCompiler görevi kullanma
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 43b7ccc11e8d265c0b1490e7e8de0bd33d903904
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036190"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler görevi

`AspNetCompiler`Görev, ASP.NET uygulamalarını önceden derlemeye yönelik bir yardımcı program olan *aspnet_compiler.exe*sarmalanmış.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tablo, görevin parametrelerini açıklar `AspNetCompiler` .

|Parametre|Açıklama|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise, `true` tanımlayıcı ad derlemesi kısmen güvenilen çağıranlara izin verir.|
|`Clean`|İsteğe bağlı `Boolean` parametre<br /><br /> Bu parametre ise `true` , önceden derlenmiş uygulama temiz oluşturulur. Önceden derlenen tüm bileşenler yeniden derlenir. Varsayılan değer: `false`. Bu parametre, *aspnet_compiler.exe*üzerindeki **-c** anahtarına karşılık gelir.|
|`Debug`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` hata ayıklama bilgileri (. PDB dosyası) derleme sırasında yayılır. Varsayılan değer: `false`. Bu parametre, *aspnet_compiler.exe*üzerindeki **-d** anahtarına karşılık gelir.|
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` , derleme oluşturulduğunda tamamen imzalanmaz.|
|`FixedNames`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` , derlenmiş derlemelere sabit adlar verilecek.|
|`Force`|İsteğe bağlı `Boolean` parametre<br /><br /> Bu parametre ise `true` , zaten varsa görev hedef dizinin üzerine yazar. Mevcut içerikler kaybedilir. Varsayılan değer: `false`. Bu parametre, *aspnet_compiler.exe*üzerindeki **-f** anahtarına karşılık gelir.|
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Bir tanımlayıcı ad anahtar kapsayıcısı belirtir.|
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Tanımlayıcı ad anahtar dosyasının fiziksel yolunu belirtir..|
|`MetabasePath`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın tam IIS metatabanı yolunu belirtir. Bu parametre `VirtualPath` veya `PhysicalPath` parametreleriyle birleştirilemez. Bu parametre, *aspnet_compiler.exe*üzerindeki **-e** anahtarına karşılık gelir.|
|`PhysicalPath`|İsteğe bağlı `String` parametre.<br /><br /> Derlenecek uygulamanın fiziksel yolunu belirtir. Bu parametre eksikse, IIS metatabanı uygulamayı bulmak için kullanılır. Bu parametre, *aspnet_compiler.exe*üzerindeki **-p** anahtarına karşılık gelir.|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametre.<br /><br /> *aspnet_compiler.exe* hangi .NET Framework sürümünün kullanılması gerektiğini belirten Targetframeworkbilinen adını belirtir. Yalnızca .NET Framework bilinen adları kabul eder.|
|`TargetPath`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın derlendiği fiziksel yolu belirtir. Belirtilmemişse, uygulama yerinde önceden derlenmiş olur.|
|`Updateable`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre ise `true` , önceden derlenmiş uygulama güncelleştirilebilir olur.  Varsayılan değer: `false`. Bu parametre, *aspnet_compiler.exe*üzerindeki **-u** anahtarına karşılık gelir.|
|`VirtualPath`|İsteğe bağlı `String` parametre.<br /><br /> Derlenecek uygulamanın sanal yolu. `PhysicalPath`Belirtilmişse, fiziksel yol, uygulamayı bulmak için kullanılır. Aksi takdirde, IIS metatabanı kullanılır ve uygulamanın varsayılan sitede olduğu varsayılır. Bu parametre, *aspnet_compiler.exe*üzerindeki **-v** anahtarına karşılık gelir.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `AspNetCompiler` bir ASP.NET uygulamasını önceden derlemek için görevini kullanır.

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
