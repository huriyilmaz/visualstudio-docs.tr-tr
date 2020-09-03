---
title: XslTransformation görevi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094549"
---
# <a name="xsltransformation-task"></a>XslTransformation görevi

Bir XSLT veya derlenmiş XSLT kullanarak bir XML girişini dönüştürür ve çıkış cihazına veya bir dosyaya çıktılar verir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `XslTransformation` .

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPaths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> XML dönüştürmesi için çıkış dosyalarını belirtir.|
|`Parameters`|İsteğe bağlı `String` parametre.<br /><br /> XSLT giriş belgesi için parametreleri belirtir.  Her parametreyi tutan ham XML sağlayın `<Parameter Name="" Value="" Namespace="" />` .|
|`XmlContent`|İsteğe bağlı `String` parametre.<br /><br /> XML girişini bir dize olarak belirtir.|
|`XmlInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> XML giriş dosyalarını belirtir.|
|`XslCompiledDllPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Derlenen XSLT 'yi belirtir.|
|`XslContent`|İsteğe bağlı `String` parametre.<br /><br /> XSLT girişini bir dize olarak belirtir.|
|`XslInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> XSLT giriş dosyasını belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte, XML dosyasını değiştirmek için bir XSL Transform dosyası *Transform. XSLT* kullanılır `$(XmlInputFileName)` . Dönüştürülmüş XML üzerine yazılır `$(IntermediateOutputPath)output.xml` . XSL dönüşümü `$(Parameter1)` bir giriş parametresi olarak alır.

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
