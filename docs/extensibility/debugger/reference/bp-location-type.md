---
title: BP_LOCATION_TYPE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737947"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Kesme noktası isteği için kesme noktasının konum türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Alanlar
`BPLT_NONE`\
Kesme noktası konumu belirtmezse.

`BPLT_FILE_LINE`\
Kesme noktasının konum türünü dosya satırı olarak belirtir.

`BPLT_FUNC_OFFSET`\
Kesme noktasının konum türünü işlev ofset olarak belirtir.

`BPLT_CONTEXT`\
Bir bağlam olarak kesme noktasının konum türünü belirtir.

`BPLT_STRING`\
Kesme noktasının konum türünü dize olarak belirtir.

`BPLT_ADDRESS`\
Kesme noktasının konum türünü adres olarak belirtir.

`BPLT_RESOLUTION`\
Kesme noktasının konum türünü çözüm olarak belirtir.

`BPLT_CODE_FILE_LINE`\
Kesme noktasının konum türünü kaynak kodu satırı olarak belirtir.

`BPLT_CODE_FUNC_OFFSET`\
Kesme noktasının konum türünü kod işlevi mahsup olarak belirtir.

`BPLT_CODE_CONTEXT`\
Kesme noktasının konum türünü kod bağlamı olarak belirtir.

`BPLT_CODE_STRING`\
Kesme noktasının konum türünü kod dizesi olarak belirtir.

`BPLT_CODE_ADDRESS`\
Kesme noktasının konum türünü kod adresi olarak belirtir.

`BPLT_DATA_STRING`\
Kesme noktasının konum türünü veri dizesi olarak belirtir.

`BPLT_TYPE_MASK`\
Kesme noktası türünün değerden çıkarılabilmeleri için biraz maske belirtir.

`BPLT_LOCATION_TYPE_MASK`\
Kesme noktası konumu türü değerden ayıklanabilmek için bir bit maskesi belirtir.

## <a name="remarks"></a>Açıklamalar
[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) yöntemine parametre olarak geçirilir.

Kesme noktası konum türü, kesme noktası türü ve konum türünden oluşur. Bu, kesme noktası konum türünün hiçbir zaman sadece bir `BPT_CODE`kesme noktası türü (örneğin) veya bir konum türü (örneğin,) `BPLT_FILE_LINE`olmadığı anlamına gelir. Şu anda desteklenen tüm kesme noktası konum türleri için önceden tanımlanmış`BPLT_CODE_FILE_LINE` sabitler bu numaralandırmaya (aracılığıyla) `BPLT_DATA_STRING`dahildir.

`BPT_CODE`ve `BPT_DATA` [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) numaralandırma üyesidir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
