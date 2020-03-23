---
title: Uygulamaları ASP.NET derlemek için AspNetCompiler Görevini Kullanma | Microsoft Dokümanlar
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
ms.openlocfilehash: 8707371fac876586d38f12a797aaee7228b5f729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634584"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler görevi

Görev `AspNetCompiler` *aspnet_compiler.exe,* ASP.NET uygulamaları önceden derlemek için bir yardımcı program sarar.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevparametreleri `AspNetCompiler` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre `true`", güçlü ad derlemesi kısmen güvenilen arayanlara izin verir.|
|`Clean`|İsteğe bağlı `Boolean` parametre<br /><br /> Bu parametre `true`ise, önceden derlenmiş uygulama temiz olarak oluşturulur. Önceden derlenmiş bileşenler yeniden derlenecektir. Varsayılan değer: `false`. Bu parametre *aspnet_compiler.exe*'deki **-c** anahtarına karşılık gelir.|
|`Debug`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre `true`ise, hata ayıklama bilgileri (. PDB dosyası) derleme sırasında yayılır. Varsayılan değer: `false`. Bu parametre *aspnet_compiler.exe'deki* **-d** anahtarına karşılık gelir.|
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre `true`ise, montaj oluşturulduğunda tam olarak imzalanmaz.|
|`FixedNames`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre `true`ise, derlenen derlemelere sabit adlar verilecektir...|
|`Force`|İsteğe bağlı `Boolean` parametre<br /><br /> Bu parametre `true`ise, görev zaten varsa hedef dizinin üzerine yazar. Varolan içerik kaybolur. Varsayılan değer: `false`. Bu parametre *aspnet_compiler.exe'deki* **-f** anahtarına karşılık gelir.|
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Güçlü bir ad anahtar kapsayıcıbelirtir.|
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Güçlü ad anahtarı dosyasına fiziksel yol belirtir...|
|`MetabasePath`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın tam IIS metabase yolunu belirtir. Bu parametre `VirtualPath` veya `PhysicalPath` parametrelerle birleştirilemez. Bu parametre *aspnet_compiler.exe'deki* **-m** anahtarına karşılık gelir.|
|`PhysicalPath`|İsteğe bağlı `String` parametre.<br /><br /> Derlenecek uygulamanın fiziksel yolunu belirtir. Bu parametre eksikse, uygulamayı bulmak için IIS metatabanı kullanılır. Bu parametre *aspnet_compiler.exe'deki* **-p** anahtarına karşılık gelir.|
|`TargetFrameworkMoniker`|İsteğe bağlı `String` parametre.<br /><br /> *aspnet_compiler.exe'nin* .NET Framework sürümünün kullanılması gerektiğini belirten TargetFrameworkMoniker belirtir. Sadece .NET Framework monikers kabul eder.|
|`TargetPath`|İsteğe bağlı `String` parametre.<br /><br /> Uygulamanın derlendiği fiziksel yolu belirtir. Belirtilmemişse, uygulama yerinde önceden derlenir.|
|`Updateable`|İsteğe bağlı `Boolean` parametre.<br /><br /> Bu parametre `true`ise, önceden derlenmiş uygulama güncelleştirilebilir.  Varsayılan değer: `false`. Bu parametre *aspnet_compiler.exe'deki* **-u** anahtarına karşılık gelir.|
|`VirtualPath`|İsteğe bağlı `String` parametre.<br /><br /> Derlenecek uygulamanın sanal yolu. Belirtilirse, `PhysicalPath` uygulamayı bulmak için fiziksel yol kullanılır. Aksi takdirde, IIS metatabanı kullanılır ve uygulamanın varsayılan sitede olduğu varsayılır. Bu parametre *aspnet_compiler.exe'deki* **-v** anahtarına karşılık gelir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [ToolTaskExtension taban sınıfına](../msbuild/tooltaskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `AspNetCompiler` ASP.NET bir uygulamayı önceden derlemek için görevi kullanır.

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
