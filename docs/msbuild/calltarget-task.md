---
title: CallTarget görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 831153a734fa88c045f7b8397db0a033e53862c7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634493"
---
# <a name="calltarget-task"></a>CallTarget görevi

Proje dosyası içinde belirtilen hedefleri çağırır.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda `CallTarget` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|---------------------------| - |
| `RunEachTargetSeparately` | İsteğe bağlı `Boolean` giriş parametresi.<br /><br /> `true`, MSBuild altyapısı her hedef için bir kez çağırılır. `false`, tüm hedefleri oluşturmak için MSBuild altyapısına bir kez çağırılır. Varsayılan değer: `false`. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Tüm oluşturulan hedeflerin çıkışlarını içerir. |
| `Targets` | İsteğe bağlı `String[]` parametresi.<br /><br /> Derlenecek hedefi veya hedefleri belirtir. |
| `UseResultsCache` | İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, önbelleğe alınan sonuç varsa döndürülür.<br /><br /> **Göz önünde** Bir MSBuild görevi çalıştırıldığında, çıktısı derleme öğelerinin listesi olarak bir kapsamda (ProjectFileName, GlobalProperties) [TargetNames] önbelleğe alınır. |

## <a name="remarks"></a>Açıklamalar

 `Targets` belirtilen bir hedef başarısız olursa ve `RunEachTargetSeparately` `true`, görev kalan hedefleri oluşturmaya devam eder.

 Varsayılan hedefleri derlemek istiyorsanız, [MSBuild görevini](../msbuild/msbuild-task.md) kullanın ve `Projects` parametresini `$(MSBuildProjectFile)`değerine ayarlayın.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek `CallOtherTargets`içinden `TargetA` çağırır.

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
- [Hedefler](../msbuild/msbuild-targets.md)
