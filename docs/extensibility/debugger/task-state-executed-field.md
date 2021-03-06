---
description: Görev çalışıyor ancak henüz tamamlanmadı.
title: TASK_STATE_EXECUTED alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6bdc6344c3257611664fc792658dcf6508e91bfd
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223296"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED alanı
Görev çalışıyor ancak henüz tamamlanmadı.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)

 Bu iç üyeye .NET Framework erişeolmadığınızdan, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Açıklamalar
 [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) alan bu değeri içeriyorsa, <xref:System.Threading.Tasks.Task.Status%2A> özelliği döndürür <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
