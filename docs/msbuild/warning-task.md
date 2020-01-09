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
ms.openlocfilehash: 84b9f9d9d92815d1719f8ba43f4014ef9598e0c4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567144"
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
| `Text` | İsteğe bağlı `String` parametresi.<br /><br /> `Condition` parametresi `true`değerlendirilirse günlüğe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] olan uyarı metni. |

## <a name="remarks"></a>Açıklamalar
 `Warning` görevi, sonraki derleme adımıyla devam etmeden önce, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projelerin gerekli bir yapılandırma veya özellik varlığını denetlemesini sağlar.

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
