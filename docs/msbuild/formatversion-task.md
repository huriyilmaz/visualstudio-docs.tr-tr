---
title: FormatVersion Görev | Microsoft Docs
description: FormatVersion görevlerinin MSBuild numarasını sürüm numarasına eklemesi için çeşitli yollar hakkında bilgi edinebilirsiniz.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2dfb1b97910858f5d6b1d59dbdbacda7a78ae73d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137127"
---
# <a name="formatversion-task"></a>FormatVersion görevi

Sürüm numarasına düzeltme numarasını ekler.

- Durum #1: Giriş: Version= \<undefined> ;  Revision= \<don't care> ;   Çıkış: OutputVersion="1.0.0.0"

- Durum #2: Giriş: Version="1.0.0.*" Revision="5" Output: OutputVersion="1.0.0.5"

- Durum #3: Giriş: Version="1.0.0.0" Revision= \<don't care> ;  Çıkış: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `FormatVersion` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`FormatType`|İsteğe `String` bağlı parametre.<br /><br /> Biçim türünü belirtir.<br /><br /> - "Sürüm" = sürüm.<br />- "Path" = replace "." with "_";|
|`OutputVersion`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Düzeltme numarasını içeren çıkış sürümünü belirtir.|
|`Revision`|İsteğe `Int32` bağlı parametre.<br /><br /> Sürüme eklenecek düzeltmeyi belirtir.|
|`Version`|İsteğe `String` bağlı parametre.<br /><br /> Biçimlendirilen sürüm numarası dizesini belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
