---
title: CallTarget görevi | Microsoft Docs
description: MSBuild CallTarget görevinin proje dosyası içinde belirtilen hedefleri çağırmak için nasıl kullanılacağını öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 3a2f124fa7e83e9f85e572276eed1851f42f7047
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939558"
---
# <a name="calltarget-task"></a>CallTarget görevi

Proje dosyası içinde belirtilen hedefleri çağırır.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tablo, görevin parametrelerini açıklar `CallTarget` .

| Parametre | Açıklama |
|---------------------------| - |
| `RunEachTargetSeparately` | İsteğe bağlı `Boolean` giriş parametresi.<br /><br /> İse `true` , MSBuild altyapısı her hedef için bir kez çağırılır. İse `false` , tüm hedefleri derlemek Için MSBuild altyapısı bir kez çağırılır. `false` varsayılan değerdir. |
| `TargetOutputs` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Tüm oluşturulan hedeflerin çıkışlarını içerir. |
| `Targets` | İsteğe bağlı `String[]` parametre.<br /><br /> Derlenecek hedefi veya hedefleri belirtir. |
| `UseResultsCache` | İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , önbelleğe alınan sonuç varsa döndürülür.<br /><br /> **Göz önünde** Bir MSBuild görevi çalıştırıldığında, çıktısı derleme öğelerinin listesi olarak bir kapsamda (ProjectFileName, GlobalProperties) [TargetNames] önbelleğe alınır. |

## <a name="remarks"></a>Açıklamalar

 Başarısız ' de belirtilen bir hedef `Targets` ve `RunEachTargetSeparately` ise `true` , görev kalan hedefleri oluşturmaya devam eder.

 Varsayılan hedefleri derlemek istiyorsanız, [MSBuild görevini](../msbuild/msbuild-task.md) kullanın ve `Projects` parametresini değerine ayarlayın `$(MSBuildProjectFile)` .

Kullanırken `CallTarget` , MSBuild, çağrılan hedefi yeni bir kapsamda olduğu gibi değerlendirir. Bu, çağrılan hedefteki herhangi bir öğe ve özellik değişikliklerinin çağıran hedefe görünmeyeceği anlamına gelir.  Çağıran hedefe bilgi geçirmek için `TargetOutputs` Çıkış parametresini kullanın.

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek içinden çağrı yapılır `TargetA` `CallOtherTargets` .

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
