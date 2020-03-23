---
title: FormatVersiyon Görevi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 250c73ce0395f278b72c18605f1666290670e20a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634116"
---
# <a name="formatversion-task"></a>FormatVersion görevi

Düzeltme numarasını sürüm numarasına ekler.

- Case #1: Giriş:\<Sürüm= tanımlanmamış>;  Revizyon=\<> umurumda değil;   Çıktı: OutputVersion="1.0.0.0"

- Örnek #2: Giriş: Sürüm="1.0.0.*" Revision="5" Çıktı: OutputVersion="1.0.0.5"

- Case #3: Giriş: Sürüm="1.0.0.0"\<Revizyon=> umurumda değil;  Çıktı: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `FormatVersion` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FormatType`|İsteğe bağlı `String` parametre.<br /><br /> Biçim türünü belirtir.<br /><br /> - "Sürüm" = sürüm.<br />- "Yol" = "_ ile "." yerine;|
|`OutputVersion`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Düzeltme numarasını içeren çıktı sürümünü belirtir.|
|`Revision`|İsteğe bağlı `Int32` parametre.<br /><br /> Sürüme eklemek için düzeltmeyi belirtir.|
|`Version`|İsteğe bağlı `String` parametre.<br /><br /> Biçimlendirmesürüm numarası dizesini belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
