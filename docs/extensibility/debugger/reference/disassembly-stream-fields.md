---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737360"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Sökme alanı hakkında hangi bilgilerin alıncaya kadar alınacak larını belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Alanlar
`DSF_ADDRESS`\
`bstrAddress` Alanı başlatma/kullanma.

`DSF_ADDRESSOFFSET`\
`bstrAddressOffset` Alanı başlatma/kullanma.

`DSF_CODEBYTES`\
`bstrCodeBytes` Alanı başlatma/kullanma.

`DSF_OPCODE`\
`bstrOpCode` Alanı başlatma/kullanma.

`DSF_OPERANDS`\
`bstrOperands` Alanı başlatma/kullanma.

`DSF_SYMBOL`\
`bstrSymbol` Alanı başlatma/kullanma.

`DSF_CODELOCATIONID`\
`uCodeLocationId` Alanı başlatma/kullanma.

`DSF_POSITION`\
Initialize/use `posBeg` the `posEnd` ve fields.

`DSF_DOCUMENTURL`\
`bstrDocumentUrl` Alanı başlatma/kullanma.

`DSF_BYTEOFFSET`\
`dwByteOffset` Alanı başlatma/kullanma.

`DSF_FLAGS`\
`dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) alanını başlatma/kullanma.

`DSF_OPERANDS_SYMBOLS`\
`bstrOperands` Alana sembol adları ekleyin.

`DSF_ALL`\
Sökme akışı için tüm alanları belirtir.

## <a name="remarks"></a>Açıklamalar
[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısının hangi alanlarının başharfe çevrileceğini belirtmek için [Okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yöntemine parametre olarak geçirilir.

`DisassemblyData` Yapının `dwFields` üyesi için hangi alanların kullanıldığını belirtmek için kullanılır ve yapı döndürüldüğünde geçerlidir.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
