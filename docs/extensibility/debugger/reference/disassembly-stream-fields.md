---
description: Ayrıştırılmış bir alan hakkında hangi bilgilerin alınması gerektiğini belirtir.
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb45f492a58bd079a1b73212fc9473041d10589
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170477"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Ayrıştırılmış bir alan hakkında hangi bilgilerin alınması gerektiğini belirtir.

## <a name="syntax"></a>Syntax

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
Alanı başlatın/kullanın `bstrAddress` .

`DSF_ADDRESSOFFSET`\
Alanı başlatın/kullanın `bstrAddressOffset` .

`DSF_CODEBYTES`\
Alanı başlatın/kullanın `bstrCodeBytes` .

`DSF_OPCODE`\
Alanı başlatın/kullanın `bstrOpCode` .

`DSF_OPERANDS`\
Alanı başlatın/kullanın `bstrOperands` .

`DSF_SYMBOL`\
Alanı başlatın/kullanın `bstrSymbol` .

`DSF_CODELOCATIONID`\
Alanı başlatın/kullanın `uCodeLocationId` .

`DSF_POSITION`\
Ve alanlarını başlatın/ `posBeg` kullanın `posEnd` .

`DSF_DOCUMENTURL`\
Alanı başlatın/kullanın `bstrDocumentUrl` .

`DSF_BYTEOFFSET`\
Alanı başlatın/kullanın `dwByteOffset` .

`DSF_FLAGS`\
`dwFlags`([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) alanını başlatın/kullanın.

`DSF_OPERANDS_SYMBOLS`\
Alana sembol adlarını ekleyin `bstrOperands` .

`DSF_ALL`\
Ayrıştırılmış akış için tüm alanları belirtir.

## <a name="remarks"></a>Açıklamalar
[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısının hangi alanlarının başlatıldığını göstermek için [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yöntemine bir parametre olarak geçirilir.

Yapı öğesi için, `dwFields` `DisassemblyData` Yapı döndürüldüğünde hangi alanların kullanıldığını ve geçerli olduğunu göstermek için kullanılır.

Bu değerler, bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Okuyamaz](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
