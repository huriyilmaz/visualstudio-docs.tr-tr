---
title: CallTarget Görev | Microsoft Docs
description: Proje dosyasında belirtilen hedefleri çağırmak MSBuild CallTarget görevini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ceafb3a687d533705d278fb0ca76496f1d27acdf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150618"
---
# <a name="calltarget-task"></a>CallTarget görevi

Proje dosyasında belirtilen hedefleri çağırır.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevin parametreleri açık `CallTarget` almaktadır.

| Parametre | Açıklama |
|---------------------------| - |
| `RunEachTargetSeparately` | İsteğe `Boolean` bağlı giriş parametresi.<br /><br /> ise, `true` MSBuild başına bir kez çağrılır. ise, `false` MSBuild tüm hedefleri oluşturmak için bir kez çağrılır. `false` varsayılan değerdir. |
| `TargetOutputs` | İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Tüm yerleşik hedeflerin çıkışlarını içerir. |
| `Targets` | İsteğe `String[]` bağlı parametre.<br /><br /> Derlemek için hedefi veya hedefleri belirtir. |
| `UseResultsCache` | İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` önbelleğe alınan sonuç varsa döndürülür.<br /><br /> **Not** Bir MSBuild çalıştırıldıklarında, çıktısı derleme öğelerinin listesi olarak bir kapsamda (ProjectFileName, GlobalProperties)[TargetNames] önbelleğe alınmış olur. |

## <a name="remarks"></a>Açıklamalar

 içinde belirtilen hedef başarısız `Targets` olursa `RunEachTargetSeparately` ve `true` ise, görev kalan hedefleri derlemeye devam eder.

 Varsayılan hedefleri oluşturmak için MSBuild [kullanın](../msbuild/msbuild-task.md) ve parametresini `Projects` değerine eşit olarak `$(MSBuildProjectFile)` ayarlayın.

kullanırken, MSBuild hedef yeni bir kapsamda değerlendirilir, ancak `CallTarget` çağrılmış olan kapsamdan farklı olarak değerlendirilir. Bu, çağrılı hedefte yapılan herhangi bir öğe ve özellik değişikliğinin, çağıran hedef için görünür olmadığını gösterir.  Çağrı hedefine bilgi geçmek için çıkış `TargetOutputs` parametresini kullanın.

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek içinden `TargetA` çağrısında `CallOtherTargets` dır.

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Targets](../msbuild/msbuild-targets.md)
