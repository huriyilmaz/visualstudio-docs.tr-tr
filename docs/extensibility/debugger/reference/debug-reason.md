---
title: DEBUG_REASON | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737428"
---
# <a name="debug_reason"></a>DEBUG_REASON
İşlemin hata ayıklama için neden başlatıldığını belirtir.

## <a name="syntax"></a>Sözdizimi

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
Belirli olmayan bir hata oluştu (diğer nedenlerden hiçbiri uymadığında bu varsayılan koşul olarak kullanılır).

`DEBUG_REASON_USER_LAUNCHED`\
İşlem, kullanıcının isteği üzerine başlatıldı.

`DEBUG_REASON_USER_ATTACHED`\
Zaten çalışan işlem kullanıcı tarafından iliştirildi.

`DEBUG_REASON_AUTO_ATTACHED`\
İşlem başlatıldığında otomatik olarak bağlandı.

`DEBUG_REASON_CAUSALITY`\
İşlem, *Just-In-Time* (JIT) hata ayıklama olayı nedeniyle başlatıldı.

## <a name="remarks"></a>Açıklamalar
[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) yönteminden döndü.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
