---
description: Görev çalışıyor ancak henüz tamamlanmadı.
title: TASK_STATE_EXECUTED Alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca0d2f578cc4e20b71e562d5b82245995bfd2969
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902858"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED alanı
Görev çalışıyor ancak henüz tamamlanmadı.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib (mscorlib.dll)

 Bu iç üyeye .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Açıklamalar
 M_stateFlags [alanı](../../extensibility/debugger/m-stateflags-field.md) bu değeri içeriyorsa özelliği <xref:System.Threading.Tasks.Task.Status%2A> değerini <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
