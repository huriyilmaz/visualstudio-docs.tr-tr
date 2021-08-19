---
title: NotifyDebuggerOfWaitCompletion Yöntemi | Microsoft Docs
description: Hata ayıklayıcı tarafından kesme noktası hedefi olarak kullanılan bir yer tutucu olan NotifyDebuggerOfWaitCompletion yöntemini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f4ba75017e277f12c6d3727ddc3d14a7dfd3483a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160380"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion yöntemi
Hata ayıklayıcı tarafından kesme noktası hedefi olarak kullanılan yer tutucu yöntemi. Bu yöntemin, büyük/büyük/büyük olması veya en iyi duruma getirilmiş olması gerekir.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Açıklamalar
 Hata ayıklayıcısı bildirim biti ayarlanmışsa, bir görevle tüm birleştirme işlemleri bu yöntemi çağırsın.

## <a name="requirements"></a>Gereksinimler

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
