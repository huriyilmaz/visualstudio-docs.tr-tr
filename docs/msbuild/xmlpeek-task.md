---
title: XmlPeek görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59bc42bd438d80bbaf0ff45cd1c95447961cd437
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630633"
---
# <a name="xmlpeek-task"></a>XmlPeek görevi

XML dosyasından XPath sorgusuyla belirtilen değerleri döndürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `XmlPeek` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Namespaces`|İsteğe bağlı `String` parametresi.<br /><br /> XPath sorgu önekleri için ad alanlarını belirtir.|
|`Query`|İsteğe bağlı `String` parametresi.<br /><br /> XPath sorgusunu belirtir.|
|`Result`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Bu görev tarafından döndürülen sonuçları içerir.|
|`XmlContent`|İsteğe bağlı `String` parametresi.<br /><br /> XML girişini bir dize olarak belirtir.|
|`XmlInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> XML girişini dosya yolu olarak belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
