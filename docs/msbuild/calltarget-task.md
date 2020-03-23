---
title: CallTarget Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: 26d29c236b89172ab6dc456be97016b98f2cae19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094563"
---
# <a name="calltarget-task"></a>CallTarget görevi

Proje dosyasında belirtilen hedefleri çağırır.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevparametreleri `CallTarget` açıklanmaktadır.

| Parametre | Açıklama |
|---------------------------| - |
| `RunEachTargetSeparately` | İsteğe bağlı `Boolean` giriş parametresi.<br /><br /> MSBuild `true`motoru hedef başına bir kez çağrılırsa. Eğer `false`, MSBuild motoru bir kez tüm hedefleri oluşturmak için denir. Varsayılan değer: `false`. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Tüm inşa edilen hedeflerin çıktılarını içerir. |
| `Targets` | İsteğe bağlı `String[]` parametre.<br /><br /> Oluşturmak için hedef veya hedefleri belirtir. |
| `UseResultsCache` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa, `true`önbelleğe alınmış sonuç varsa döndürülür.<br /><br /> **Not** Bir MSBuild görevi çalıştırıldığında, çıktısı yapı öğeleri listesi olarak bir kapsamda (ProjectFileName, GlobalProperties)[TargetNames] önbelleğe alır. |

## <a name="remarks"></a>Açıklamalar

 Belirtilen bir hedef `Targets` başarısız `RunEachTargetSeparately` `true`olursa ve başarısız olursa, görev kalan hedefleri oluşturmaya devam eder.

 Varsayılan hedefleri oluşturmak istiyorsanız, [MSBuild görevini](../msbuild/msbuild-task.md) kullanın ve `Projects` parametreyi `$(MSBuildProjectFile)`' ye eşit olarak ayarlayın

MsBuild, kullanırken, `CallTarget`çağrılan hedefi, çağrıldığı kapsamın aksine, yeni bir kapsamda değerlendirir. Bu, çağrılan hedefteki herhangi bir öğe ve özellik değişikliğinin çağıran hedef tarafından görülemeden olduğu anlamına gelir.  Aramayı hedefe bilgi aktarmak için `TargetOutputs` çıktı parametresini kullanın.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek `TargetA` içeriden `CallOtherTargets`çağırır.

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
- [Hedef](../msbuild/msbuild-targets.md)
