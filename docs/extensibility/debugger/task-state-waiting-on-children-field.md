---
title: TASK_STATE_WAITING_ON_CHILDREN Alanı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27b9963db54d939b3d509da451478c20dbe0e7d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712578"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN alanı
Görev temsilcisini yürütmeyi tamamladı ve dolaylı olarak eklenen alt görevlerin tamamlanmasını bekliyor.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

 Bu iç üyeye .NET Framework'den erişemediğinizden, aşağıdaki sözdizimi Ortak Ara Dil 'de (CIL) sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Açıklamalar
 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) alanı bu değeri içeriyorsa, <xref:System.Threading.Tasks.Task.Status%2A> özellik döndürür. <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
