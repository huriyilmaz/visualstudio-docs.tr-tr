---
description: Kesme noktası isteği hakkında alınacak bilgileri belirtir.
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f7ee5d8dbf48ad8d1b07512727b1b91635ab990
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162465"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Kesme noktası isteği hakkında alınacak bilgileri belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Alanlar
`BPREQI_BPLOCATION`\
`bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) veya [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapısının (kesme noktası konumu) alanını başlatın/kullanın.

`BPREQI_LANGUAGE`\
`guidLanguage`Veya yapısının alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_PROGRAM`\
`pProgram`Veya yapısının alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_PROGRAMNAME`\
`bstrProgramName`Veya yapısının alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_THREAD`\
`pThread`Veya yapısının alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_THREADNAME`\
`bstrThreadName`Veya yapısının alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_PASSCOUNT`\
`bpPassCount`Veya yapısının alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_CONDITION`\
`bpCondition`Veya yapısının (kesme noktası koşulu) alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_FLAGS`\
`dwFlags`Veya yapısının alanını başlatın/kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI_ALLOLDFIELDS`\
Yapının tüm alanlarını başlatın/kullanın `BP_REQUEST_INFO` .

`BPREQI_VENDOR`\
Yapı alanını başlatın/kullanın `guidVendor` `BP_REQUEST_INFO2` .

`BPREQI_CONSTRAINT`\
Yapı alanını başlatın/kullanın `bstrConstraint` `BP_REQUEST_INFO2` .

`BPREQI_TRACEPOINT`\
Yapı alanını başlatın/kullanın `bstrTracepoint` `BP_REQUEST_INFO2` .

`BPREQI_ALLFIELDS`\
Yapının tüm alanlarını belirtir `BP_REQUEST_INFO2` .

## <a name="remarks"></a>Açıklamalar
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapılarının hangi alanlarının başlatıldığını belirtmek için [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) ve [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yöntemlerine bir bağımsız değişken olarak geçirilir.

Bu bayraklar Ayrıca, `BP_REQUEST_INFO` ve yapıların hangi alanlarının `BP_REQUEST_INFO2` kullanıldığını ve her bir yapı döndürüldüğünde geçerli olduğunu göstermek için kullanılır.

Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
