---
title: İleti görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c570a5a783133f9422dc434d0ef460b9ca7510e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633492"
---
# <a name="message-task"></a>İleti görevi

Derleme sırasında bir iletiyi günlüğe kaydeder.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `Message` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Importance`|İsteğe bağlı `String` parametresi.<br /><br /> İletinin önemini belirtir. Bu parametre `high`, `normal` veya `low`değerine sahip olabilir. Varsayılan değer: `normal`.|
|`Text`|İsteğe bağlı `String` parametresi.<br /><br /> Günlüğe kaydedilecek hata metni.|

## <a name="remarks"></a>Açıklamalar

 `Message` görevi, MSBuild projelerinin derleme işlemindeki farklı adımlarda oturum cihazlarına ileti vermesini sağlar.

 `Condition` parametresi `true`değerlendirilirse, `Text` parametresinin değeri günlüğe kaydedilir ve derleme yürütülmeye devam eder. Bir `Condition` parametresi yoksa ileti metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

 Varsayılan olarak, ileti MSBuild konsol günlükçüsü öğesine gönderilir. Bu, <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametresi ayarlanarak değiştirilebilir. Günlükçü `Importance` parametresini yorumlar. Genellikle, günlükçü ayrıntı düzeyi <xref:Microsoft.Build.Framework.LoggerVerbosity>`Minimal` veya üzeri olarak ayarlandığında `high` olarak ayarlanmış bir ileti gönderilir. Günlükçü ayrıntı düzeyi <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`olarak ayarlandığında `low` olarak ayarlanmış bir ileti gönderilir.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, tüm kayıtlı Günlükçüler için iletileri günlüğe kaydeder.

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
- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
