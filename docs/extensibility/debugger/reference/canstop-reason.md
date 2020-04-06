---
title: CANSTOP_REASON | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7be361d4468584c109db52f487b3de3c1fdff0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737687"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Bir programın yürütmede belirli bir noktaya ulaştıktan sonra yürütmeyi durdurup durduramayacağına karar vermek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Alanlar
`CANSTOP_ENTRYPOINT`\
Verilen programın giriş noktasını belirtir.

`CANSTOP_STEPIN`\
Bir işleve adım atma belirtir.

## <a name="remarks"></a>Açıklamalar
Programın giriş noktasına ulaştıktan sonra veya bir işlev veya yönteme adım attıktan sonra durdurmak için tamam ise Oturum Hata Ayıklama Yöneticisi (SDM) ile onaylamak için [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) yöntemine bir argüman olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
