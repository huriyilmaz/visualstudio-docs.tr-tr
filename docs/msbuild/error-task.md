---
title: Hata görevi | Microsoft Docs
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
ms.openlocfilehash: 7e09fa38f9f160728c3ca353164e87c9f3f6fa82
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596365"
---
# <a name="error-task"></a>Hata görevi
Bir derlemeyi durdurup değerlendirilen bir koşullu ifadeye göre bir hata kaydeder.

## <a name="parameters"></a>Parametreler
Aşağıdaki tabloda `Error` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe bağlı `String` parametresi.<br /><br /> Hatayla ilişkilendirilecek hata kodu. |
| `File` | İsteğe bağlı `String` parametresi.<br /><br /> Hatayı içeren dosyanın adı. Dosya adı sağlanmazsa, hata görevini içeren dosya kullanılacaktır. |
| `HelpKeyword` | İsteğe bağlı `String` parametresi.<br /><br /> Hatayla ilişkilendirilecek Yardım anahtar sözcüğü. |
| `Text` | İsteğe bağlı `String` parametresi.<br /><br /> `Condition` parametresi `true`değerlendirildiğinde günlüğe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] olan hata metni. |

## <a name="remarks"></a>Açıklamalar
`Error` görevi [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projelerin günlüğe hata metni vermesini ve derleme yürütmeyi durdurmasını sağlar.

`Condition` parametresi `true`değerlendirilirse, derleme durdurulur ve bir hata günlüğe kaydedilir. Bir `Condition` parametresi yoksa, hata günlüğe kaydedilir ve derleme yürütmesi duraklar. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki kod örneği, tüm gerekli özelliklerinin ayarlandığını doğrular. Bunlar ayarlanmamışsa, proje bir hata olayı oluşturur ve `Error` görevinin `Text` parametresinin değerini günlüğe kaydeder.

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
- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
