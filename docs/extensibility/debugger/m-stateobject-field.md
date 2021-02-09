---
title: m_stateObject alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bbf16af65ab59147614ce5609de9b56ff833862a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925134"
---
# <a name="m_stateobject-field"></a>m_stateObject alanı
Eylemin kullanacağı verileri temsil eden nesne.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

 Bu iç üyeye .NET Framework erişeolmadığınızdan, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Açıklamalar
 Bu, `state` <xref:System.Threading.Tasks.Task.%23ctor%2A> kurucudaki parametredir. Ayrıca, özelliği için de yedekleme alanıdır <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> .

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
