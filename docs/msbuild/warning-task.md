---
title: Uyarı Görevi | Microsoft Docs
description: Değerlendirme MSBuild bir derleme sırasında uyarıyı günlüğe kaydedilirken Uyarı görevini nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 9906e901d1d793e80a6e099b1f003659515bf6e3
ms.sourcegitcommit: 1d44a5509772c3926f5ad13b1796485d6d8c441e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135963927"
---
# <a name="warning-task"></a>Uyarı görevi

Değerlendirilen koşullu deyimi temel alan bir derleme sırasında bir uyarıyı günlüğe kaydeder.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `Warning` almaktadır.

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe `String` bağlı parametre.<br /><br /> Uyarıyla ilişkilendirilen uyarı kodu. |
| `File` | İsteğe `String` bağlı parametre.<br /><br /> Varsa ilgili dosyayı belirtir. Hiçbir dosya sağlanmazsa, Uyarı görevini içeren dosya kullanılır. |
| `HelpKeyword` | İsteğe `String` bağlı parametre.<br /><br /> Uyarıyla ilişkilendirilen Yardım anahtar sözcüğü. Yalnızca dahili kullanım içindir. |
| `HelpLink` | İsteğe `String` bağlı parametre.<br/><br /> Uyarı hakkında daha fazla bilgi için bir bağlantı. |
| `Text` | İsteğe `String` bağlı parametre.<br /><br /> Parametresinin değerlendirmesi MSBuild günlüğe `Condition` kaydeden uyarı `true` metni. |

## <a name="remarks"></a>Açıklamalar

 Görev, MSBuild bir sonraki derleme adımına devam etmeden önce gerekli yapılandırmanın veya özelliğin `Warning` varlığını denetlemeye olanak sağlar.

 Görevin `Condition` parametresi olarak `Warning` değerlendirilirse parametrenin değeri günlüğe kaydedilir ve derleme `true` `Text` yürütülmaya devam eder. Parametre `Condition` yoksa uyarı metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için [bkz. Derleme günlüklerini alma.](../msbuild/obtaining-build-logs-with-msbuild.md)

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

`HelpKeyword`, Visual Studio (F1) özelliğini desteklemek için kullanılır. Çevrimiçi yardım `HelpLink` sayfasını bir hata iletisiyle ilişkilendirmek için kullanabilirsiniz.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, komut satırına ayarlanmış özellikleri denetler. Ayarlanmış bir özellik yoksa proje bir uyarı olayı verir ve görevin parametresinin `Text` değerini günlüğe `Warning` kaydeder.

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

- [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
