---
title: DISASSEMBLY_FLAGS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737379"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Sökme için bayrakları belirtir.

## <a name="syntax"></a>Sözdizimi

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
Bu yönerge, öncekinden farklı bir belgede olduğunu gösterir.

`DF_DISABLED`\
Bu talimatın yürütülmeyeceğini gösterir.

`DF_INSTRUCTION_ACTIVE`\
Bu talimatın yürütülecek sonraki yönergelerden biri olduğunu gösterir (birden fazla olabilir).

`DF_DATA`\
Bu talimatın gerçekten veri (kod değil) olduğunu gösterir.

`DF_HASSOURCE`\
Bu talimatın kaynağı olduğunu gösterir. Profil oluşturma veya çöp toplama kodu gibi bazı yönergelerin karşılık gelen bir kaynağı yoktur.

`DF_DOCUMENT_CHECKSUM`\
`bstrDocumentUrl` Alanın belge URL'sinden sonra checksum verileri içerdiğini gösterir. Denetimler verisinin nasıl depolandırılabildiğini [disassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısıiçin Açıklamalar bölümüne bakın.

## <a name="remarks"></a>Açıklamalar
`dwFlags` [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısının üyesi olarak kullanılır.

Bu bayraklar biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
