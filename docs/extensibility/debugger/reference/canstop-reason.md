---
description: Bir programın yürütmede belirli bir noktaya ulaştıktan sonra yürütmeyi durduranın olup olmadığını belirlemek için kullanılır.
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a9b61c9c77c015071e3661865b93575cb8bbb98
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635153"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Bir programın yürütmede belirli bir noktaya ulaştıktan sonra yürütmeyi durduranın olup olmadığını belirlemek için kullanılır.

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
Bir işleve adımlama belirtir.

## <a name="remarks"></a>Açıklamalar
Oturum Hata Ayıklama Yöneticisi'ne (SDM) programın giriş noktasına ulaştıktan sonra veya bir işleve ya da yönteme adımlamanın ardından durmasının uygun olup olduğunu onaylamak için [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) yöntemine bağımsız değişken olarak geçirildi.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
