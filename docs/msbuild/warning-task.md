---
title: Uyarı Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631100"
---
# <a name="warning-task"></a>Uyarı görevi

Değerlendirilmiş koşullu bir bildirime dayalı bir yapı sırasında bir uyarı yığlar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `Warning` açıklanmaktadır.

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe bağlı `String` parametre.<br /><br /> Uyarı ile ilişkilendirmek için uyarı kodu. |
| `File` | İsteğe bağlı `String` parametre.<br /><br /> Varsa ilgili dosyayı belirtir. Dosya sağlanmadıysa, Uyarı görevini içeren dosya kullanılır. |
| `HelpKeyword` | İsteğe bağlı `String` parametre.<br /><br /> Uyarıyla ilişkilendirmek için Yardım anahtar sözcüğü. |
| `Text` | İsteğe bağlı `String` parametre.<br /><br /> `Condition` Parametre ' nin değerlendirilmesi durumunda MSBuild'in günlük olduğu uyarı `true`metni. |

## <a name="remarks"></a>Açıklamalar

 Görev, `Warning` MSBuild projelerinin bir sonraki yapı adımına geçmeden önce gerekli yapılandırmaveya özelliğin varlığını denetlemesine olanak tanır.

 Görevin `Condition` parametresi `true`değerlendirirse, `Text` parametrenin değeri günlüğe kaydedilir ve yapı yürütmeye devam eder. `Warning` Parametre `Condition` yoksa, uyarı metni günlüğe kaydedilir. Günlüğe kaydetme hakkında daha fazla bilgi için [bkz.](../msbuild/obtaining-build-logs-with-msbuild.md)

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği komut satırında ayarlanan özellikleri denetler. Ayarlanmış özellikler yoksa, proje bir uyarı olayı yükseltir ve `Text` `Warning` görevin parametresinin değerini günlüğe kaydeder.

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

- [Yapı günlükleri edinme](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
