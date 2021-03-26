---
description: Ayrıştırılmış derleme bayraklarını belirtir.
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28335176a70213f61bfbb77bf6f91cc6155902e7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096206"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Ayrıştırılmış derleme bayraklarını belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Alanlar
`DF_DOCUMENTCHANGE`\
Bu yönergenin öncekinden farklı bir belgede olduğunu gösterir.

`DF_DISABLED`\
Bu yönergenin yürütülemeyecek olduğunu gösterir.

`DF_INSTRUCTION_ACTIVE`\
Bu yönergenin yürütülecek sonraki yönergelerden biri olduğunu belirtir (birden fazla olabilir).

`DF_DATA`\
Bu yönergenin gerçekten veri (kod değil) olduğunu gösterir.

`DF_HASSOURCE`\
Bu yönergenin kaynak olduğunu gösterir. Profil oluşturma veya çöp toplama kodu gibi bazı yönergelere karşılık gelen bir kaynak yoktur.

`DF_DOCUMENT_CHECKSUM`\
Bu `bstrDocumentUrl` alanın, belge URL 'sinden sonra sağlama toplamı verilerini içerdiğini belirtir. Sağlama toplamı verilerinin nasıl depolandığını gösteren [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısına ilişkin açıklamalar bölümüne bakın.

## <a name="remarks"></a>Açıklamalar
`dwFlags` [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısının üyesi olarak kullanılır.

Bu bayraklar bit düzeyinde birleştirilebilir `OR` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
