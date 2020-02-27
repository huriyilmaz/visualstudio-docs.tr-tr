---
title: Uyarı görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e95b59b4ccc0bd2df89e45512a5bdd05c027556
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631100"
---
# <a name="warning-task"></a>Uyarı görevi

Değerlendirilen bir koşullu ifadeye dayanan bir derleme sırasında bir uyarı kaydeder.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `Warning` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe bağlı `String` parametresi.<br /><br /> Uyarıyla ilişkilendirilecek uyarı kodu. |
| `File` | İsteğe bağlı `String` parametresi.<br /><br /> Varsa ilgili dosyayı belirtir. Dosya sağlanmazsa, uyarı görevini içeren dosya kullanılır. |
| `HelpKeyword` | İsteğe bağlı `String` parametresi.<br /><br /> Uyarıyla ilişkilendirilecek Yardım anahtar sözcüğü. |
| `Text` | İsteğe bağlı `String` parametresi.<br /><br /> `Condition` parametresi `true`olarak değerlendirilirse, MSBuild 'in kaydettiği uyarı metni. |

## <a name="remarks"></a>Açıklamalar

 `Warning` görevi, MSBuild projelerinin bir sonraki derleme adımına geçmeden önce gerekli bir yapılandırmanın veya özelliğin varlığını denetlemesini sağlar.

 `Warning` görevinin `Condition` parametresi `true`olarak değerlendirilirse, `Text` parametresinin değeri günlüğe kaydedilir ve derleme yürütülmeye devam eder. Bir `Condition` parametresi yoksa, uyarı metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, komut satırında ayarlanan özellikleri denetler. Hiçbir özellik ayarlanmamışsa, proje bir uyarı olayı oluşturur ve `Warning` görevinin `Text` parametresinin değerini günlüğe kaydeder.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme günlüklerini al](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
