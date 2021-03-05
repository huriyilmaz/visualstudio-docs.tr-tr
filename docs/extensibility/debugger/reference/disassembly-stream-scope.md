---
description: Ayrıştırılmış akışın kapsamını belirtir.
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c688da1c850743f92fb9b87f7f5d72fb66d946d6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170451"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Ayrıştırılmış akışın kapsamını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Alanlar
`DSS_HUGE`\
Kod bağlamının ayırt edilen bir istemciden genellikle tek bir çağrıda almak isteyenden daha fazla çıkış üretebileceğinizi belirtir.

`DSS_FUNCTION`\
Kod bağlamı tarafından içerilen işlevin ayrıştırılmış olması gerektiğini belirtir. Ayrıştırılmış birleştirme akışının [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) yöntemi tarafından döndürüldüğünde bir işlevi temsil ettiğini belirtir.

`DSS_MODULE`\
Yöntemi tarafından döndürüldüğünde `IDebugDisassemblyStream2::GetScope` , ayrıştırılmış birleştirme akışının bir modülü temsil ettiğini belirtir.

`DSS_ALL`\
Tüm adres alanı için ayrıştırılmış kodu belirtir.

## <a name="remarks"></a>Açıklamalar
[Getdisassemblystream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) yöntemine bir bağımsız değişken olarak geçirilir ve [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) yöntemi tarafından döndürülür.

Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
