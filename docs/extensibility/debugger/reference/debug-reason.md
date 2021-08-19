---
description: İşlemin hata ayıklama için neden başlat olduğunu belirtir.
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 493328f0dbad03030c3f817177a5adb4dc213bc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160289"
---
# <a name="debug_reason"></a>DEBUG_REASON
İşlemin hata ayıklama için neden başlat olduğunu belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Alanlar
`DEBUG_REASON_ERROR`\
Özel olmayan bir hata oluştu (diğer nedenlerden hiçbiri uygun olduğunda varsayılan koşul olarak kullanılır).

`DEBUG_REASON_USER_LAUNCHED`\
İşlem kullanıcının isteği üzerine başlatıldı.

`DEBUG_REASON_USER_ATTACHED`\
Zaten çalışan işlem, kullanıcı tarafından 'a ekli.

`DEBUG_REASON_AUTO_ATTACHED`\
İşlem, başlatıldıklarından otomatik olarak eklenir.

`DEBUG_REASON_CAUSALITY`\
İşlem bir Tam Zamanında (JIT) *hata* ayıklama olayı nedeniyle başlatıldı.

## <a name="remarks"></a>Açıklamalar
[GetDebugReason yönteminden](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
