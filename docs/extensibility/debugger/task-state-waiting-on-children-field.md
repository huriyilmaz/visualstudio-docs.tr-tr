---
description: Görev, temsilcisini yürütmeyi tamamladı ve ekli alt görevlerin tamamlanması için örtülü olarak bekliyor.
title: TASK_STATE_WAITING_ON_CHILDREN Alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6e63ef2032b4d3ac2bd874276c690b84a36b4abaf598b9eb44a37fca810ad1b1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306237"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN alanı
Görev, temsilcisini yürütmeyi tamamladı ve ekli alt görevlerin tamamlanması için örtülü olarak bekliyor.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

 Bu iç üyeye .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Açıklamalar
 M_stateFlags [alanı](../../extensibility/debugger/m-stateflags-field.md) bu değeri içeriyorsa özelliği <xref:System.Threading.Tasks.Task.Status%2A> değerini <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
