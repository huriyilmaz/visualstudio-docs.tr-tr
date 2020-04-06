---
title: BPREQI_FIELDS90 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737738"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Kesme noktası isteği hakkında alınacak bilgileri belirten geçerli değerleri oyalar. Bu numaralandırma [numaralandırma BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) genişletir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Alanlar
`BPREQI90_BPLOCATION`\
`bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) veya [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapısının (kesme noktası konumu) alanını başlatma veya kullanma.

`BPREQI90_LANGUAGE`\
Veya `guidLanguage` `BP_REQUEST_INFO` `BP_REQUEST_INFO2` yapının alanını başlatma veya kullanma.

`BPREQI90_PROGRAM`\
Veya `pProgram` `BP_REQUEST_INFO` `BP_REQUEST_INFO2` yapının alanını başlatma veya kullanma.

`BPREQI90_PROGRAMNAME`\
Veya `bstrProgramName` `BP_REQUEST_INFO` `BP_REQUEST_INFO2` yapının alanını başlatma veya kullanma.

`BPREQI90_THREAD`\
Veya `pThread` `BP_REQUEST_INFO` `BP_REQUEST_INFO2` yapının alanını başlatma veya kullanma.

`BPREQI90_THREADNAME`\
Veya `bstrThreadName` `BP_REQUEST_INFO` `BP_REQUEST_INFO2` yapının alanını başlatma veya kullanma.

`BPREQI90_PASSCOUNT`\
Veya `bpPassCount` `BP_REQUEST_INFO` `BP_REQUEST_INFO2` yapının alanını başlatma veya kullanma.

`BPREQI90_CONDITION`\
(Kesme noktası `bpCondition` koşulu) alanını başlatma `BP_REQUEST_INFO` veya `BP_REQUEST_INFO2` kullanma.

`BPREQI90_FLAGS`\
Veya `dwFlags` `BP_REQUEST_INFO` `BP_REQUEST_INFO2` yapının alanını başlatma veya kullanma.

`BPREQI90_ALLOLDFIELDS`\
`BP_REQUEST_INFO` Yapının tüm alanlarını başlatma veya kullanma.

`BPREQI90_VENDOR`\
`BP_REQUEST_INFO2` Yapı `guidVendor` alanını başlatma veya kullanma.

`BPREQI90_CONSTRAINT`\
`BP_REQUEST_INFO2` Yapı `bstrConstraint` alanını başlatma veya kullanma.

`BPREQI90_TRACEPOINT`\
`BP_REQUEST_INFO2` Yapı `bstrTracepoint` alanını başlatma veya kullanma.

`BPREQI90_MACROTRACEPOINT`\
`BP_REQUEST_INFO2` Yapı `bstrMacroTracepoint` alanını başlatma veya kullanma. BPREQI_ALLFIELDS bu alanı içermez.

`BPREQI90_ALLFIELDS`\
`BP_REQUEST_INFO2` Yapı için tüm alanları belirtir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: Msdbg90.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
