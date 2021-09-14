---
description: Görev çalışıyor ancak henüz tamamlanmadı.
title: TASK_STATE_EXECUTED alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c7617d0b54c2fe2532eb92b54810e7e9d8a28d7c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626385"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED alanı
Görev çalışıyor ancak henüz tamamlanmadı.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)

 bu iç üyeye .NET Framework erişeolmadığınızdan, ortak ara dil (cıl) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Açıklamalar
 [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) alan bu değeri içeriyorsa, <xref:System.Threading.Tasks.Task.Status%2A> özelliği döndürür <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
