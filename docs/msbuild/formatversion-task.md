---
title: FormatVersion görevi | Microsoft Docs
description: MSBuild FormatVersion görevlerinin, Düzeltme numarasını sürüm numarasına nasıl ekleyeceğinden ilgili çeşitli yollar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6444811750a59de5488b8ca3614f9926d472746
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905484"
---
# <a name="formatversion-task"></a>FormatVersion görevi

Sürüm numarasına Düzeltme numarasını ekler.

- Örnek #1: giriş: sürüm = \<undefined> ;  Düzeltme = \<don't care> ;   Çıkış: OutputVersion = "1.0.0.0"

- Case #2: Input: Version = "1.0.0. *" Revision = "5" çıkış: OutputVersion = "1.0.0.5"

- Case #3: Input: Version = "1.0.0.0" Düzeltme = \<don't care> ;  Çıkış: OutputVersion = "1.0.0.0"

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `FormatVersion` .

|Parametre|Açıklama|
|---------------|-----------------|
|`FormatType`|İsteğe bağlı `String` parametre.<br /><br /> Biçim türünü belirtir.<br /><br /> -"Sürüm" = sürüm.<br />-"Path" = "." yerine "_";|
|`OutputVersion`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Düzeltme numarasını içeren çıkış sürümünü belirtir.|
|`Revision`|İsteğe bağlı `Int32` parametre.<br /><br /> Sürüme eklenecek düzeltmeyi belirtir.|
|`Version`|İsteğe bağlı `String` parametre.<br /><br /> Biçimlendirilecek sürüm numarası dizesini belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
