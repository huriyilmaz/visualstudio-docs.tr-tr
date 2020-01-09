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
ms.openlocfilehash: 90b56d3b36545ecfe97015fc301ce3ce72e781ba
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588375"
---
# <a name="xsltransformation-task"></a>XslTransformation görevi
Bir XSLT veya derlenmiş XSLT kullanarak bir XML girişini dönüştürür ve çıkış cihazına veya bir dosyaya çıktılar verir.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `XslTransformation` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`OutputPaths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> XML dönüştürmesi için çıkış dosyalarını belirtir.|
|`Parameters`|İsteğe bağlı `String` parametresi.<br /><br /> XSLT giriş belgesi için parametreleri belirtir.|
|`XmlContent`|İsteğe bağlı `String` parametresi.<br /><br /> XML girişini bir dize olarak belirtir.|
|`XmlInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> XML giriş dosyalarını belirtir.|
|`XslCompiledDllPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Derlenen XSLT 'yi belirtir.|
|`XslContent`|İsteğe bağlı `String` parametresi.<br /><br /> XSLT girişini bir dize olarak belirtir.|
|`XslInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> XSLT giriş dosyasını belirtir.|

## <a name="remarks"></a>Açıklamalar
 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
