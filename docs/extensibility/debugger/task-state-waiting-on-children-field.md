---
description: Görev, temsilcisini yürütmeyi bitirdi ve ekli alt görevlerin tamamlanmasını örtük olarak bekliyor.
title: TASK_STATE_WAITING_ON_CHILDREN alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1533ef28b32450d9b039c27e49ba655dddfd6ebe
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223217"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN alanı
Görev, temsilcisini yürütmeyi bitirdi ve ekli alt görevlerin tamamlanmasını örtük olarak bekliyor.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

 Bu iç üyeye .NET Framework erişeolmadığınızdan, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Açıklamalar
 [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) alan bu değeri içeriyorsa, <xref:System.Threading.Tasks.Task.Status%2A> özelliği döndürür <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
