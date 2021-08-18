---
description: İşlenemeyen bir özel durum nedeniyle görev tamamlandı.
title: TASK_STATE_FAULTED Alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7a603ace4218acfeb412fc50389c8484cdcdb3a6ce79eacb347e9c8957590a53
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432949"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED alanı
İşlenemeyen bir özel durum nedeniyle görev tamamlandı.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

 Bu iç üyeye .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Açıklamalar
 M_stateFlags [alanı](../../extensibility/debugger/m-stateflags-field.md) bu değeri içeriyorsa <xref:System.Threading.Tasks.Task.Status%2A> özelliği <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
