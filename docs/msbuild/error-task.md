---
title: Hata Görevi | Microsoft Docs
description: Bir derlemeyi MSBuild ve değerlendirilen koşullu deyime göre bir hatayı günlüğe günlük kaydı yapmak için MSBuild Error görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ad3b206dbbbc65b2a3a08bc4bee7e8a4e4e85773
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108973"
---
# <a name="error-task"></a>Hata görevi

Bir derlemeyi durdurur ve değerlendirilen koşullu deyime göre bir hatayı günlüğe kaydeder.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `Error` almaktadır.

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe `String` bağlı parametre.<br /><br /> Hatayla ilişkilendirilen hata kodu. |
| `File` | İsteğe `String` bağlı parametre.<br /><br /> Hatayı içeren dosyanın adı. Hiçbir dosya adı sağlanmayacaksa, Hata görevini içeren dosya kullanılır. |
| `HelpKeyword` | İsteğe `String` bağlı parametre.<br /><br /> Hatayla ilişkilendirilen Yardım anahtar sözcüğü. |
| `Text` | İsteğe `String` bağlı parametre.<br /><br /> Parametresinin değerlendirmesi MSBuild `Condition` günlüklere kaydeden hata `true` metni. |

## <a name="remarks"></a>Açıklamalar

Bu `Error` görev, MSBuild projelerinin günlüklere hata metni oluşturmasını ve derleme yürütmesini durdurmasını sağlar.

parametresi `Condition` olarak değerlendirilirse `true` derleme durdurulur ve bir hata günlüğe kaydedilir. Parametre `Condition` yoksa hata günlüğe kaydedilir ve derleme yürütmesi durdurulur. Günlüğe kaydetme hakkında daha fazla bilgi için [bkz. Derleme günlüklerini alma.](../msbuild/obtaining-build-logs-with-msbuild.md)

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki kod örneği tüm gerekli özelliklerin ayar olduğunu doğrular. Ayarlanmazsa, proje bir hata olayı döndürür ve görevin parametresinin `Text` değerini günlüğe `Error` kaydeder.

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
- [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md)
