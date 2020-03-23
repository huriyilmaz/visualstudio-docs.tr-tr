---
title: XslDönüşüm Görevi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d23799e5ce5bf391915ac459c69c27b990211f0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094549"
---
# <a name="xsltransformation-task"></a>XslTransformation görevi

XSLT veya derlenmiş XSLT kullanarak xml girdisini dönüştüren ve çıktıları bir çıkış aygıtına veya dosyaya dönüştürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `XslTransformation` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPaths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> XML dönüşümü için çıktı dosyalarını belirtir.|
|`Parameters`|İsteğe bağlı `String` parametre.<br /><br /> Parametreleri XSLT Giriş belgesine belirtir.  Her parametreyi ' olarak tutan `<Parameter Name="" Value="" Namespace="" />`ham XML'yi sağlayın.|
|`XmlContent`|İsteğe bağlı `String` parametre.<br /><br /> XML girişini dize olarak belirtir.|
|`XmlInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> XML giriş dosyalarını belirtir.|
|`XslCompiledDllPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Derlenen XSLT'yi belirtir.|
|`XslContent`|İsteğe bağlı `String` parametre.<br /><br /> XSLT girişini bir dize olarak belirtir.|
|`XslInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> XSLT giriş dosyasını belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, xml dosyasını `$(XmlInputFileName)`değiştirmek için xsl dönüştürme dosyası *transform.xslt* kullanılır. Dönüştürülmüş XML' ye `$(IntermediateOutputPath)output.xml`yazılır. XSL dönüşümü `$(Parameter1)` giriş parametresi olarak alır.

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
