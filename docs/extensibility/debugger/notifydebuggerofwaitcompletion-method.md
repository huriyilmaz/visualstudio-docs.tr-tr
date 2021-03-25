---
title: NotifyDebuggerOfWaitCompletion yöntemi | Microsoft Docs
description: Hata ayıklayıcı tarafından kesme noktası hedefi olarak kullanılan bir yer tutucu olan NotifyDebuggerOfWaitCompletion yöntemi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d58bb7a5e3a3395b534e5679ec303e5d93d5dc85
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054744"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion yöntemi
Hata ayıklayıcı tarafından bir kesme noktası hedefi olarak kullanılan yer tutucu yöntemi. Bu yöntem satır içine alınmalıdır veya iyileştirilmemelidir.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Açıklamalar
 Bir görevle tüm JOIN işlemleri, hata ayıklayıcı bildirim biti ayarlandıysa bu yöntemi çağırmalıdır.

## <a name="requirements"></a>Gereksinimler

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
