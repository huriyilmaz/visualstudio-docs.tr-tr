---
title: TASK_STATE_CANCELED Alanı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712755"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED alanı
Görev çalışan duruma ulaşmadan önce iptal edildi veya iptalini doğruladı ve istisnasız tamamlandı.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib (mscorlib.dll olarak)

 Bu iç üyeye .NET Framework'den erişemediğinizden, aşağıdaki sözdizimi Ortak Ara Dil 'de (CIL) sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Açıklamalar
 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) alanı bu değeri içeriyorsa, <xref:System.Threading.Tasks.Task.Status%2A> özellik döndürür. <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
