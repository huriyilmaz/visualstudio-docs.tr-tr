---
title: BPREQI_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737756"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Kesme noktası isteği hakkında alınacak bilgileri belirtir.

## <a name="syntax"></a>Sözdizimi

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
`bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) veya [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapısının (kırılma noktası konumu) alanını başlatma/kullanma.

`BPREQI_LANGUAGE`\
Alanın `guidLanguage` `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` yapının alanını başlatma/kullanma.

`BPREQI_PROGRAM`\
Alanın `pProgram` `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` yapının alanını başlatma/kullanma.

`BPREQI_PROGRAMNAME`\
Alanın `bstrProgramName` `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` yapının alanını başlatma/kullanma.

`BPREQI_THREAD`\
Alanın `pThread` `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` yapının alanını başlatma/kullanma.

`BPREQI_THREADNAME`\
Alanın `bstrThreadName` `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` yapının alanını başlatma/kullanma.

`BPREQI_PASSCOUNT`\
Alanın `bpPassCount` `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` yapının alanını başlatma/kullanma.

`BPREQI_CONDITION`\
(Kesme noktası `bpCondition` koşulu) alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_FLAGS`\
Alanın `dwFlags` `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` yapının alanını başlatma/kullanma.

`BPREQI_ALLOLDFIELDS`\
`BP_REQUEST_INFO` Yapının tüm alanlarını başlatma/kullanma.

`BPREQI_VENDOR`\
`BP_REQUEST_INFO2` Yapı `guidVendor` alanını başlatma/kullanma.

`BPREQI_CONSTRAINT`\
`BP_REQUEST_INFO2` Yapı `bstrConstraint` alanını başlatma/kullanma.

`BPREQI_TRACEPOINT`\
`BP_REQUEST_INFO2` Yapı `bstrTracepoint` alanını başlatma/kullanma.

`BPREQI_ALLFIELDS`\
`BP_REQUEST_INFO2` Yapı için tüm alanları belirtir.

## <a name="remarks"></a>Açıklamalar
[GetRequestInfo'ya](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) ve [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapıların hangi alanlarının baş harfe başlatIflaştırılaolacağını belirtmek için [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yöntemlerine bir argüman olarak geçirilir.

Bu bayraklar, her yapı döndürüldüğünde hangi alanların `BP_REQUEST_INFO` kullanıldığını ve `BP_REQUEST_INFO2` geçerli olduğunu belirtmek için de kullanılır.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
