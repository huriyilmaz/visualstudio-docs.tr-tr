---
title: Hata görevi | Microsoft Docs
description: bir derlemeyi durdurmak ve değerlendirilen bir koşullu ifadeye dayanarak bir hatayı günlüğe kaydetmek için MSBuild hata görevini kullanın.
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
ms.openlocfilehash: 25051888bcabf288f90d8315a17ffc6432a521a4
ms.sourcegitcommit: 1d44a5509772c3926f5ad13b1796485d6d8c441e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135963947"
---
# <a name="error-task"></a>Hata görevi

Bir derlemeyi durdurup değerlendirilen bir koşullu ifadeye göre bir hata kaydeder.

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini açıklar `Error` .

| Parametre | Açıklama |
|---------------| - |
| `Code` | İsteğe bağlı `String` parametre.<br /><br /> Hatayla ilişkilendirilecek hata kodu. |
| `File` | İsteğe bağlı `String` parametre.<br /><br /> Hatayı içeren dosyanın adı. Dosya adı sağlanmazsa, hata görevini içeren dosya kullanılacaktır. |
| `HelpKeyword` | İsteğe bağlı `String` parametre.<br /><br /> Hatayla ilişkilendirilecek Yardım anahtar sözcüğü. Yalnızca dahili kullanım içindir. |
| `HelpLink` | İsteğe bağlı `String` parametre.<br/><br /> Hata hakkında daha fazla bilgi için bir bağlantı. |
| `Text` | İsteğe bağlı `String` parametre.<br /><br /> `Condition`parametresi olarak değerlendirilirse MSBuild hata metni `true` . |

## <a name="remarks"></a>Açıklamalar

`Error`görev MSBuild projelerin günlüğe hata metni vermesini ve derleme yürütmeyi durdurmasını sağlar.

`Condition`Parametresi olarak değerlendirilirse `true` , derleme durdurulur ve bir hata günlüğe kaydedilir. Bir `Condition` parametre yoksa, hata günlüğe kaydedilir ve derleme yürütmesi duraklar. Günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md).

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

`HelpKeyword`, Visual Studio tarafından bağlamsal yardım özelliğini (F1) desteklemek için kullanılır. `HelpLink`Çevrimiçi yardım sayfasını bir hata iletisiyle ilişkilendirmek için ' i kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, tüm gerekli özelliklerinin ayarlandığını doğrular. Bunlar ayarlanmamışsa, proje bir hata olayı oluşturur ve görevin parametresinin değerini günlüğe kaydeder `Text` `Error` .

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
