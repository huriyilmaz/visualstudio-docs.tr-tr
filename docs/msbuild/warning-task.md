---
title: Uyarı görevi | Microsoft Docs
description: MSBuild, değerlendirilen bir koşullu ifadeye dayalı bir derleme sırasında uyarı kaydetmek için uyarı görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: faf53415b62550cb2091ffc9741ed2eeef60bbcc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076938"
---
# <a name="warning-task"></a>Uyarı görevi

Değerlendirilen bir koşullu ifadeye dayanan bir derleme sırasında bir uyarı kaydeder.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `Warning` .

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe bağlı `String` parametre.<br /><br /> Uyarıyla ilişkilendirilecek uyarı kodu. |
| `File` | İsteğe bağlı `String` parametre.<br /><br /> Varsa ilgili dosyayı belirtir. Dosya sağlanmazsa, uyarı görevini içeren dosya kullanılır. |
| `HelpKeyword` | İsteğe bağlı `String` parametre.<br /><br /> Uyarıyla ilişkilendirilecek Yardım anahtar sözcüğü. |
| `Text` | İsteğe bağlı `String` parametre.<br /><br /> parametresi olarak değerlendirilirse MSBuild olan uyarı metni `Condition` `true` . |

## <a name="remarks"></a>Açıklamalar

 görev, bir `Warning` sonraki derleme adımına geçmeden önce, MSBuild projelerin gerekli bir yapılandırma veya özellik varlığını denetlemesini sağlar.

 `Condition` `Warning` Görevin parametresi olarak değerlendirilirse `true` , `Text` parametrenin değeri günlüğe kaydedilir ve derleme yürütülmeye devam eder. Bir `Condition` parametre yoksa, uyarı metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, komut satırında ayarlanan özellikleri denetler. Hiçbir özellik ayarlanmamışsa, proje bir uyarı olayı oluşturur ve görevin parametresinin değerini günlüğe kaydeder `Text` `Warning` .

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
- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
