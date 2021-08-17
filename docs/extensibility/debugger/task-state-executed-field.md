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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c7617d0b54c2fe2532eb92b54810e7e9d8a28d7c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042640"
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
 M_stateFlags [alanı](../../extensibility/debugger/m-stateflags-field.md) bu değeri içeriyorsa <xref:System.Threading.Tasks.Task.Status%2A> özelliği değerini <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
