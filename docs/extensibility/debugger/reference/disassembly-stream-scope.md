---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737265"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Sökme akışının kapsamını belirtir.

## <a name="syntax"></a>Sözdizimi

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
Kod bağlamını sökmenin, istemcinin genellikle tek bir çağrıda almak isteyeceğinden daha fazla çıktı oluşturacağını belirtir.

`DSS_FUNCTION`\
Kod bağlamı tarafından bulunan işlevin sökülmesi gerektiğini belirtir. Sökme akışının [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) yöntemiyle döndürüldüğünde bir işlevi temsil ettiğini belirtir.

`DSS_MODULE`\
`IDebugDisassemblyStream2::GetScope` Yöntem tarafından döndürüldüğünde, sökme akışının bir modülü temsil ettiğini belirtir.

`DSS_ALL`\
Tüm adres alanı için sökme belirtir.

## <a name="remarks"></a>Açıklamalar
[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) yöntemine bağımsız değişken olarak geçirilir ve [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) yöntemi yle döndürülür.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
