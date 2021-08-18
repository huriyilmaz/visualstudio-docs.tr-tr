---
title: İleti Görevi | Microsoft Docs
description: Derlemeler sırasında iletileri günlüğe kaydeden MSBuild görev için parametreler ve ayarlar hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0b9ee3a2514d89c5b2d436666b2ff512feb8a1b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077211"
---
# <a name="message-task"></a>İleti görevi

Derleme sırasında bir iletiyi günlüğe kaydeder.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `Message` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Importance`|İsteğe `String` bağlı parametre.<br /><br /> İletinin önemini belirtir. Bu parametre , veya `high` değerine `normal` sahip `low` olabilir. `normal` varsayılan değerdir.|
|`Text`|İsteğe `String` bağlı parametre.<br /><br /> Günlüğe kaydedilirken hata metni.|

## <a name="remarks"></a>Açıklamalar

 Bu `Message` görev, MSBuild projelerinin derleme işleminin farklı adımlarında günlükçilere ileti göndermelerini sağlar.

 parametresi `Condition` olarak `true` değerlendirilirse parametrenin değeri `Text` günlüğe kaydedilir ve derleme yürütülya devam eder. Parametre `Condition` yoksa ileti metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için [bkz. Derleme günlüklerini alma.](../msbuild/obtaining-build-logs-with-msbuild.md)

 Varsayılan olarak, ileti tüm kayıtlı günlüklere gönderilir. Günlükleyici parametresini `Importance` yorumlar. Günlükçer ayrıntılılığı olarak ayarlanırsa genellikle olarak `high` ayarlanmış bir ileti <xref:Microsoft.Build.Framework.LoggerVerbosity> gönderilir.`Minimal` veya daha yüksek bir değere sahip olabilir. Günlükçer `low` ayrıntılılığı olarak ayarlanırken olarak ayarlanmış bir ileti <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` gönderilir.

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği iletileri tüm kayıtlı günlüklere kaydeder.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md)
