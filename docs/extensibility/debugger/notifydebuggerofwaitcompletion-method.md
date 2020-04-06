---
title: NotifyDebuggerOfWaitCompletion Yöntemi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738338"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion yöntemi
Yer tutucu yöntemi hata ayıklama tarafından kesme noktası hedefi olarak kullanılır. Bu yöntem inlined veya optimize edilmemelidir.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

## <a name="syntax"></a>Sözdizimi

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Açıklamalar
 Bir görevle tüm birleştirme işlemleri, hata ayıklama bildirim biti ayarlanmışsa bu yöntemi aramalıdır.

## <a name="requirements"></a>Gereksinimler

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
