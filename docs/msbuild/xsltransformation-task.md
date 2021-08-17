---
title: XslTransformation Görev | Microsoft Docs
description: XSLT MSBuild xml girişini bir çıkış cihazına veya dosyasına dönüştürmek için XslTransformation görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: db5d8254ee428f35ee495fd514a42523bd488ce9d225365e6c2884d1df4a7e05
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397078"
---
# <a name="xsltransformation-task"></a>XslTransformation görevi

XSLT veya derlenmiş XSLT kullanarak XML girişini ve çıkışları bir çıkış cihazına veya dosyaya dönüştürer.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `XslTransformation` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPaths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> XML dönüştürmesi için çıkış dosyalarını belirtir.|
|`Parameters`|İsteğe `String` bağlı parametre.<br /><br /> XSLT Giriş belgesinin parametrelerini belirtir.  Her parametreyi olarak tutan ham XML'yi `<Parameter Name="" Value="" Namespace="" />` girin.|
|`XmlContent`|İsteğe `String` bağlı parametre.<br /><br /> XML girişini dize olarak belirtir.|
|`XmlInputPaths`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> XML giriş dosyalarını belirtir.|
|`XslCompiledDllPath`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Derlenmiş XSLT'i belirtir.|
|`XslContent`|İsteğe `String` bağlı parametre.<br /><br /> XSLT girişini dize olarak belirtir.|
|`XslInputPath`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> XSLT giriş dosyasını belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnekte xml dosyasını değiştirmek için bir XSL dönüşüm dosyası *transform.xslt* `$(XmlInputFileName)` kullanılmıştır. Dönüştürülen XML, içine `$(IntermediateOutputPath)output.xml` yazılır. XSL dönüşümü bir `$(Parameter1)` giriş parametresi olarak alır.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Parametreleri](/dotnet/standard/data/xml/xslt-parameters)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
