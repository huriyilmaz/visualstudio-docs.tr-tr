---
description: Kesme noktası isteğinin konum türünü belirtir.
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 794da0fdccdeee1da47181e5d243bd22734602b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120458"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Kesme noktası isteğinin konum türünü belirtir.

## <a name="syntax"></a>Syntax

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
Kesme noktası konumunu belirtir.

`BPLT_FILE_LINE`\
Kesme noktası konum türünü bir dosya satırı olarak belirtir.

`BPLT_FUNC_OFFSET`\
Kesme noktası konum türünü işlev uzaklığı olarak belirtir.

`BPLT_CONTEXT`\
Kesme noktası konum türünü bağlam olarak belirtir.

`BPLT_STRING`\
Kesme noktası konum türünü dize olarak belirtir.

`BPLT_ADDRESS`\
Kesme noktası konum türünü adres olarak belirtir.

`BPLT_RESOLUTION`\
Çözümleme olarak kesme noktası konum türünü belirtir.

`BPLT_CODE_FILE_LINE`\
Kaynak kodu satırı olarak kesme noktası konum türünü belirtir.

`BPLT_CODE_FUNC_OFFSET`\
Kesme noktası konum türünü kod işlevi uzaklığı olarak belirtir.

`BPLT_CODE_CONTEXT`\
Kesme noktası konum türünü kod bağlamı olarak belirtir.

`BPLT_CODE_STRING`\
Kesme noktası konum türünü kod dizesi olarak belirtir.

`BPLT_CODE_ADDRESS`\
Kesme noktası konum türünü kod adresi olarak belirtir.

`BPLT_DATA_STRING`\
Kesme noktası konum türünü bir veri dizesi olarak belirtir.

`BPLT_TYPE_MASK`\
Bir bit maskesi belirtir, böylece kesme noktası türü değerin dışında ayıklanır.

`BPLT_LOCATION_TYPE_MASK`\
Bir bit maskesi belirtir, böylece kesme noktası konumu türü değerin dışında ayıklanır.

## <a name="remarks"></a>Açıklamalar
[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) yöntemine parametre olarak geçirildi.

Kesme noktası konum türü bir kesme noktası türünden ve konum türünden oluşur. Bu, kesme noktası konum türünün hiçbir zaman yalnızca bir kesme noktası türü (örneğin, ) veya konum türü `BPT_CODE` (örneğin, ) olduğu anlamına `BPLT_FILE_LINE` gelir. Şu anda desteklenen tüm kesme noktası konum türleri için önceden tanımlanmış sabitler bu sabit listesine (aracılığıyla) `BPLT_CODE_FILE_LINE` dahil `BPLT_DATA_STRING` edilir.

`BPT_CODE`ve `BPT_DATA` , BP_TYPE [](../../../extensibility/debugger/reference/bp-type.md) üyesidir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
