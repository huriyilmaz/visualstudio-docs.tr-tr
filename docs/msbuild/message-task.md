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
ms.openlocfilehash: c5a2e2a1adb810a8468d318298747eec226846df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592184"
---
# <a name="message-task"></a>İleti görevi
Derleme sırasında bir iletiyi günlüğe kaydeder.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `Message` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Importance`|İsteğe bağlı `String` parametresi.<br /><br /> İletinin önemini belirtir. Bu parametre `high`, `normal` veya `low`değerine sahip olabilir. Varsayılan değer `normal` şeklindedir.|
|`Text`|İsteğe bağlı `String` parametresi.<br /><br /> Günlüğe kaydedilecek hata metni.|

## <a name="remarks"></a>Açıklamalar
 `Message` görevi, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projelerin derleme işlemindeki farklı adımlarda oturum cihazlarına ileti vermesine olanak tanır.

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
