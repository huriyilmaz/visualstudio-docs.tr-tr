---
description: Kesme noktası isteği için kesme noktasının konum türünü belirtir.
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bb3ea3220c6b4be74e0767f0e88ab1b46d2685c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096713"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Kesme noktası isteği için kesme noktasının konum türünü belirtir.

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
Kesme noktası konumu belirtir.

`BPLT_FILE_LINE`\
Kesme noktasının konum türünü bir dosya çizgisi olarak belirtir.

`BPLT_FUNC_OFFSET`\
Kesme noktasının konum türünü işlev boşluğu olarak belirtir.

`BPLT_CONTEXT`\
Kesme noktasının konum türünü bağlam olarak belirtir.

`BPLT_STRING`\
Kesme noktasının konum türünü bir dize olarak belirtir.

`BPLT_ADDRESS`\
Kesme noktasının konum türünü bir adres olarak belirtir.

`BPLT_RESOLUTION`\
Kesme noktasının konum türünü bir çözüm olarak belirtir.

`BPLT_CODE_FILE_LINE`\
Kesme noktasının konum türünü kaynak kodu satırı olarak belirtir.

`BPLT_CODE_FUNC_OFFSET`\
Kesme noktasının konum türünü kod işlev boşluğu olarak belirtir.

`BPLT_CODE_CONTEXT`\
Kesme noktasının konum türünü kod bağlamı olarak belirtir.

`BPLT_CODE_STRING`\
Kesme noktasının konum türünü kod dizesi olarak belirtir.

`BPLT_CODE_ADDRESS`\
Kesme noktasının konum türünü kod adresi olarak belirtir.

`BPLT_DATA_STRING`\
Kesme noktasının konum türünü bir veri dizesi olarak belirtir.

`BPLT_TYPE_MASK`\
Kesme noktası türünün değerden ayıklanabilmesi için bir bit maskesini belirtir.

`BPLT_LOCATION_TYPE_MASK`\
Kesme noktası konum türünün değerden ayıklanabilmesi için bir bit maskesini belirtir.

## <a name="remarks"></a>Açıklamalar
[Getlocationtype](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) metoduna parametre olarak geçirildi.

Kesme noktası konum türü, kesme noktası türünden ve bir konum türünden oluşur. Bu, bir kesme noktası konum türünün hiçbir şekilde yalnızca bir kesme noktası türü (örneğin, `BPT_CODE` ) veya bir konum türü olduğu anlamına gelir (örneğin, `BPLT_FILE_LINE` ). Şu anda desteklenen tüm kesme noktası konum türleri için önceden tanımlanmış sabitler, bu sabit listesine ( `BPLT_CODE_FILE_LINE` üzerinden `BPLT_DATA_STRING` ) dahildir.

`BPT_CODE``BPT_DATA` [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) sabit listesi üyeleridir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
