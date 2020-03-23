---
title: VCToolTask Sınıf | Microsoft Dokümanlar
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591677"
---
# <a name="vctooltask-base-class"></a>VCToolTask taban sınıfı

Birçok görev sonuçta sınıf <xref:Microsoft.Build.Utilities.Task> ve [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) sınıfından devralınır. Bu sınıf, bunlardan türeyen görevlere çeşitli parametreler ekler. Bu parametreler bu belgede listelenmiştir.

## <a name="parameters"></a>Parametreler

Aşağıdaki **tabloda VCToolTask** taban sınıfının parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**ActiveToolSwitchesDeğerler**|İsteğe bağlı **Sözlük\<dizesi, ToolSwitch>** parametresi.|
|**Ek Seçenekler**|İsteğe bağlı **dize** parametresi.|
|**Etkili Çalışma Rehberi**|İsteğe bağlı **dize** parametresi.|
|**EtkinleştirErrorListRegex**|İsteğe bağlı **bool** parametresi.<br/><br/>`true` varsayılan değerdir.|
|**ErrorListRegex**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**ErrorListListDışlama**|İsteğe bağlı **ITaskItem[]** parametresi.|
|**Komut Hattı Oluşturma**|İsteğe bağlı **dize** parametresi.<br/><br/>**CommandLineFormat** *formatı* [default = CommandLineFormat.ForBuildLog] ve **EscapeFormat escapeFormat** *escapeFormat* [default = EscapeFormat.Default] değerlerini kullanır.|
|**KomutSatır Anahtarları Oluşturma**|İsteğe bağlı **dize** parametresi.<br/><br/>Değerleri **string[]** *anahtarlarıToRemove*, **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog], ve **EscapeFormat escapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)<br/>
[Görevler](../msbuild/msbuild-tasks.md)
