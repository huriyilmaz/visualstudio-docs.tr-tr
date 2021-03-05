---
description: Bir programın yürütmenin belirli bir noktaya ulaştıktan sonra yürütmeyi durdurup durdurmadığını tespit etmek için kullanılır.
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: def5bdbb6433f6a154eb6f84a88fb39004bc41ae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171004"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Bir programın yürütmenin belirli bir noktaya ulaştıktan sonra yürütmeyi durdurup durdurmadığını tespit etmek için kullanılır.

## <a name="syntax"></a>Syntax

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
Bir işleve adımlamayı belirtir.

## <a name="remarks"></a>Açıklamalar
Programın giriş noktasına ulaştıktan sonra veya bir işlev ya da yönteme adımladıktan sonra durmak gerekirse, oturum hata ayıklama Yöneticisi (SDM) ile onaylamak için [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) yöntemine bir bağımsız değişken olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
