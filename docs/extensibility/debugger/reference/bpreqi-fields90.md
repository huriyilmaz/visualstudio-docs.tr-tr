---
description: Bir kesme noktası isteği hakkında alınacak bilgileri belirten geçerli değerleri numaralar.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635174"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Bir kesme noktası isteği hakkında alınacak bilgileri belirten geçerli değerleri numaralar. Bu numaralama, tüm [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) genişlettir.

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
Veri yapısının `bpLocation` (kesme noktası konumu) alanını [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) [](../../../extensibility/debugger/reference/bp-request-info2.md) BP_REQUEST_INFO2 kullanın.

`BPREQI90_LANGUAGE`\
veya yapısının `guidLanguage` alanını başlatma veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullanma.

`BPREQI90_PROGRAM`\
veya yapısının `pProgram` alanını başlatma veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullanma.

`BPREQI90_PROGRAMNAME`\
veya yapısının `bstrProgramName` alanını başlatma veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullanma.

`BPREQI90_THREAD`\
veya yapısının `pThread` alanını başlatma veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullanma.

`BPREQI90_THREADNAME`\
veya yapısının `bstrThreadName` alanını başlatma veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullanma.

`BPREQI90_PASSCOUNT`\
veya yapısının `bpPassCount` alanını başlatma veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullanma.

`BPREQI90_CONDITION`\
veya yapısının `bpCondition` (kesme noktası koşulu) alanını başlat veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullan.

`BPREQI90_FLAGS`\
veya yapısının `dwFlags` alanını başlatma veya `BP_REQUEST_INFO` `BP_REQUEST_INFO2` kullanma.

`BPREQI90_ALLOLDFIELDS`\
yapı için tüm alanları başlat veya `BP_REQUEST_INFO` kullan.

`BPREQI90_VENDOR`\
Yapı alanını başlatma `guidVendor` veya `BP_REQUEST_INFO2` kullanma.

`BPREQI90_CONSTRAINT`\
Yapı alanını başlatma `bstrConstraint` veya `BP_REQUEST_INFO2` kullanma.

`BPREQI90_TRACEPOINT`\
Yapı alanını başlatma `bstrTracepoint` veya `BP_REQUEST_INFO2` kullanma.

`BPREQI90_MACROTRACEPOINT`\
Yapı alanını başlatma `bstrMacroTracepoint` veya `BP_REQUEST_INFO2` kullanma. BPREQI_ALLFIELDS alanı dahil değildir.

`BPREQI90_ALLFIELDS`\
Yapı için tüm alanları `BP_REQUEST_INFO2` belirtir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Msdbg90.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
