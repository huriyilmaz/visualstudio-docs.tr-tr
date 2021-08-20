---
description: Kesme noktası isteği hakkında alınacak bilgileri belirten geçerli değerleri sıralar.
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 859da0750f3522ae8a889612ae13db43816aa4d1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145750"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Kesme noktası isteği hakkında alınacak bilgileri belirten geçerli değerleri sıralar. Bu sabit listesi [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) numaralandırmayı genişletir.

## <a name="syntax"></a>Syntax

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
`bpLocation` [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) veya [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapısının (kesme noktası konumu) alanını başlatın veya kullanın.

`BPREQI90_LANGUAGE`\
`guidLanguage`Veya yapısının alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_PROGRAM`\
`pProgram`Veya yapısının alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_PROGRAMNAME`\
`bstrProgramName`Veya yapısının alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_THREAD`\
`pThread`Veya yapısının alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_THREADNAME`\
`bstrThreadName`Veya yapısının alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_PASSCOUNT`\
`bpPassCount`Veya yapısının alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_CONDITION`\
`bpCondition`Veya yapısının (kesme noktası koşulu) alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_FLAGS`\
`dwFlags`Veya yapısının alanını başlatın veya kullanın `BP_REQUEST_INFO` `BP_REQUEST_INFO2` .

`BPREQI90_ALLOLDFIELDS`\
Yapının tüm alanlarını başlatın veya kullanın `BP_REQUEST_INFO` .

`BPREQI90_VENDOR`\
Yapı alanını başlatın veya kullanın `guidVendor` `BP_REQUEST_INFO2` .

`BPREQI90_CONSTRAINT`\
Yapı alanını başlatın veya kullanın `bstrConstraint` `BP_REQUEST_INFO2` .

`BPREQI90_TRACEPOINT`\
Yapı alanını başlatın veya kullanın `bstrTracepoint` `BP_REQUEST_INFO2` .

`BPREQI90_MACROTRACEPOINT`\
Yapı alanını başlatın veya kullanın `bstrMacroTracepoint` `BP_REQUEST_INFO2` . BPREQI_ALLFIELDS bu alanı içermez.

`BPREQI90_ALLFIELDS`\
Yapının tüm alanlarını belirtir `BP_REQUEST_INFO2` .

## <a name="requirements"></a>Gereksinimler
Üstbilgi: Msdbg90. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
