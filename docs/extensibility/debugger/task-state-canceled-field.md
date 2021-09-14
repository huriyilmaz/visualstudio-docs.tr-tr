---
description: Görev, çalışma durumuna ulaşmadan iptal edildi veya iptalini onayladı ve özel durum olmadan tamamlandı.
title: TASK_STATE_CANCELED Alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8ea74eb264f6706fb02b03304e50baa4ee86207f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626391"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED alanı
Görev, çalışma durumuna ulaşmadan iptal edildi veya iptalini onayladı ve özel durum olmadan tamamlandı.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib (mscorlib.dll)

 Bu iç üyeye .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Açıklamalar
 M_stateFlags [alanı](../../extensibility/debugger/m-stateflags-field.md) bu değeri içeriyorsa <xref:System.Threading.Tasks.Task.Status%2A> özelliği <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
