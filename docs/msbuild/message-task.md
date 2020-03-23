---
title: İleti Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 264ff3a5e64b756020648e888f7817e12702659f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865368"
---
# <a name="message-task"></a>İleti görevi

Yapı sırasında bir iletiyi günlüğe kaydeder.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `Message` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Importance`|İsteğe bağlı `String` parametre.<br /><br /> İletinin önemini belirtir. Bu parametre `high`, `normal` veya `low`. Varsayılan değer: `normal`.|
|`Text`|İsteğe bağlı `String` parametre.<br /><br /> Günlüğe kaydacak hata metni.|

## <a name="remarks"></a>Açıklamalar

 Görev, `Message` MSBuild projelerinin oluşturma işleminde farklı adımlarda kaydedicilere ileti ler vermesine olanak tanır.

 `Condition` Parametre `true`değerlendirirse, `Text` parametrenin değeri günlüğe kaydedilir ve yapı yürütmeye devam eder. Bir `Condition` parametre yoksa, ileti metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için [bkz.](../msbuild/obtaining-build-logs-with-msbuild.md)

 Varsayılan olarak, ileti tüm kayıtlı günlüğe kaydedenlere gönderilir. Kaydedici parametreyi `Importance` yorumlar. Genellikle, logger ayrıntılı `high` olarak ayarlandığında bir ileti <xref:Microsoft.Build.Framework.LoggerVerbosity>ayarlanır.`Minimal` veya daha yüksek. Logger ayrıntılı `low` olarak ayarlandığında ayarlanan bir <xref:Microsoft.Build.Framework.LoggerVerbosity>ileti gönderilir. `Detailed`.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, tüm kayıtlı kaydedicilere iletileri kaydeder.

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
- [Yapı günlükleri edinme](../msbuild/obtaining-build-logs-with-msbuild.md)
