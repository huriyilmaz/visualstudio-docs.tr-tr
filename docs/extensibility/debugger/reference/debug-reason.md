---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737428"
---
# <a name="debug_reason"></a>DEBUG_REASON
İşlemin neden hata ayıklama için başlatıldığına ilişkin belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Alanlar
`DEBUG_REASON_ERROR`\
Belirli olmayan bir hata oluştu (diğer nedenlerden hiçbiri uygun olmadığında bu varsayılan koşul olarak kullanılır).

`DEBUG_REASON_USER_LAUNCHED`\
İşlem kullanıcının isteğiyle başlatılmıştı.

`DEBUG_REASON_USER_ATTACHED`\
Zaten çalışan işlem, Kullanıcı tarafından öğesine eklendi.

`DEBUG_REASON_AUTO_ATTACHED`\
İşlem başlatıldığı zaman otomatik olarak eklendi.

`DEBUG_REASON_CAUSALITY`\
*Tam zamanında* (JIT) hata ayıklama olayı nedeniyle işlem başlatıldı.

## <a name="remarks"></a>Açıklamalar
[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) yönteminden döndürüldü.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
