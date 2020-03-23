---
title: Hata Görevi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5dd3214c9575a34e9265c33061b024648a221c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634233"
---
# <a name="error-task"></a>Hata görevi

Yapıyı durdurur ve değerlendirilmiş koşullu deyimi temel alan bir hatayı günlüğe kaydeder.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevparametreleri `Error` açıklanmaktadır.

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe bağlı `String` parametre.<br /><br /> Hata ile ilişkilendirmek için hata kodu. |
| `File` | İsteğe bağlı `String` parametre.<br /><br /> Hatayı içeren dosyanın adı. Dosya adı sağlanmazsa, Hata görevini içeren dosya kullanılır. |
| `HelpKeyword` | İsteğe bağlı `String` parametre.<br /><br /> Hatayla ilişkilendirmek için Yardım anahtar sözcüğü. |
| `Text` | İsteğe bağlı `String` parametre.<br /><br /> `Condition` Parametre ' nin `true`değerlendirilmesi durumunda MSBuild'in günlük olduğu hata metni. |

## <a name="remarks"></a>Açıklamalar

Görev, `Error` MSBuild projelerinin loggers'a hata metni vermesini ve yapı yürütmesini durdurmasına olanak tanır.

`Condition` Parametre , yapı `true`durdurulur ve bir hata günlüğe kaydedilir değerlendirilmesi. Bir `Condition` parametre yoksa, hata günlüğe kaydedilir ve yürütme yapısı durur. Günlüğe kaydetme hakkında daha fazla bilgi için [bkz.](../msbuild/obtaining-build-logs-with-msbuild.md)

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, gerekli tüm özelliklerin ayarlı olduğunu doğrular. Bunlar ayarlanmazsa, proje bir hata olayı yükseltir ve `Text` `Error` görevin parametresinin değerini günlüğe kaydeder.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Yapı günlükleri edinme](../msbuild/obtaining-build-logs-with-msbuild.md)
