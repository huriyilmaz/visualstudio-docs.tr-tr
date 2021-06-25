---
description: System.Threading.Tasks.Task nesnesinin geçerli durumuyla ilgili bilgileri depolar.
title: m_stateFlags Alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0bf584511bc2f0ee43429abe83dea3d7a45259d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898919"
---
# <a name="m_stateflags-field"></a>m_stateFlags alanı
Nesnenin geçerli durumuyla ilgili bilgileri <xref:System.Threading.Tasks.Task> depolar.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

 Bu iç üyeye .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>Açıklamalar
 Bu değere erişmek <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> için genellikle özelliğini kullanırsiniz.

 Bu üye aşağıdaki değerlerin herhangi bir birleşimi olabilir:

- [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

- [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

- [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

- [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

- [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
