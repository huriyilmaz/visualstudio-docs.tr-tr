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
ms.openlocfilehash: 264ff3a5e64b756020648e888f7817e12702659f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78865368"
---
# <a name="message-task"></a>İleti görevi

Derleme sırasında bir iletiyi günlüğe kaydeder.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `Message` .

|Parametre|Açıklama|
|---------------|-----------------|
|`Importance`|İsteğe bağlı `String` parametre.<br /><br /> İletinin önemini belirtir. Bu parametre, veya değerine sahip olabilir `high` `normal` `low` . Varsayılan değer: `normal`.|
|`Text`|İsteğe bağlı `String` parametre.<br /><br /> Günlüğe kaydedilecek hata metni.|

## <a name="remarks"></a>Açıklamalar

 `Message`Görev, MSBuild projelerinin derleme işlemindeki farklı adımlarda günlüğe ileti vermesine izin verir.

 `Condition`Parametresi olarak değerlendirilirse `true` , `Text` parametrenin değeri günlüğe kaydedilir ve derleme yürütülmeye devam eder. Bir `Condition` parametre yoksa, ileti metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

 Varsayılan olarak, ileti tüm kayıtlı günlükçülere gönderilir. Günlükçü, parametreyi Yorumlar `Importance` . Genellikle, `high` günlükçü ayrıntı düzeyi olarak ayarlandığında, olarak ayarlanmış bir ileti gönderilir <xref:Microsoft.Build.Framework.LoggerVerbosity> .`Minimal` veya üzeri. `low`Günlükçü ayrıntı düzeyi olarak ayarlandığında, olarak ayarlanmış bir ileti gönderilir <xref:Microsoft.Build.Framework.LoggerVerbosity> . `Detailed` .

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

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
