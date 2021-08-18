---
description: Bir kesme noktası isteği hakkında alınacak bilgileri belirtir.
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88288b6d3c57e65f5f59f580468bde3180f877c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120237"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Bir kesme noktası isteği hakkında alınacak bilgileri belirtir.

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
Veri yapısının `bpLocation` (kesme noktası konumu) alanını [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) kullanın.

`BPREQI_LANGUAGE`\
veya yapısının `guidLanguage` alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_PROGRAM`\
veya yapısının `pProgram` alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_PROGRAMNAME`\
veya yapısının `bstrProgramName` alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_THREAD`\
veya yapısının `pThread` alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_THREADNAME`\
veya yapısının `bstrThreadName` alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_PASSCOUNT`\
veya yapısının `bpPassCount` alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_CONDITION`\
veya yapısının `bpCondition` (kesme noktası koşulu) alanını `BP_REQUEST_INFO` başlat/kullan. `BP_REQUEST_INFO2`

`BPREQI_FLAGS`\
veya yapısının `dwFlags` alanını `BP_REQUEST_INFO` başlatma/kullanma. `BP_REQUEST_INFO2`

`BPREQI_ALLOLDFIELDS`\
Yapının tüm alanlarını `BP_REQUEST_INFO` başlat/kullan.

`BPREQI_VENDOR`\
Yapı alanını `guidVendor` `BP_REQUEST_INFO2` başlatma/kullanma.

`BPREQI_CONSTRAINT`\
Yapı alanını `bstrConstraint` `BP_REQUEST_INFO2` başlatma/kullanma.

`BPREQI_TRACEPOINT`\
Yapı alanını `bstrTracepoint` `BP_REQUEST_INFO2` başlatma/kullanma.

`BPREQI_ALLFIELDS`\
Yapı için tüm alanları `BP_REQUEST_INFO2` belirtir.

## <a name="remarks"></a>Açıklamalar
[GetRequestInfo'ya](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) bağımsız değişken olarak geçirildi ve BP_REQUEST_INFO ve BP_REQUEST_INFO [](../../../extensibility/debugger/reference/bp-request-info.md) ve BP_REQUEST_INFO2 [](../../../extensibility/debugger/reference/bp-request-info2.md) hangi alanların başlat olacağını belirtmek için yöntemleri kullanır. [](../../../extensibility/debugger/reference/bp-request-info.md)

Bu bayraklar, ve yapılarının hangi alanlarının, `BP_REQUEST_INFO` `BP_REQUEST_INFO2` her yapı döndürülürken kullanılan ve geçerli olduğunu belirtmek için de kullanılır.

Bu değerler bitwise ile birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
