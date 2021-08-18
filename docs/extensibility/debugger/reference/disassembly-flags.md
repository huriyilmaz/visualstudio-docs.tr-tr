---
description: Ayrım için bayrakları belirtir.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4640ee39a936318b5e200fc46135e1fc271c46b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120003"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Ayrım için bayrakları belirtir.

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
Bu yönergenin yürütülmayacak olduğunu gösterir.

`DF_INSTRUCTION_ACTIVE`\
Bu yönergenin yürütülecek sonraki yönergelerden biri olduğunu gösterir (birden fazla olabilir).

`DF_DATA`\
Bu yönergenin gerçekten veri (kod değil) olduğunu gösterir.

`DF_HASSOURCE`\
Bu yönergenin kaynağı olduğunu gösterir. Profil oluşturma veya çöp toplama kodu gibi bazı yönergelere karşılık gelen bir kaynak yoktur.

`DF_DOCUMENT_CHECKSUM`\
Alanın belge `bstrDocumentUrl` URL'sinin ardından sağlama toplama verilerini içerdiğini gösterir. Sağlama toplama verilerini depolama hakkında bilgi için [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısının Açıklamalar bölümüne bakın.

## <a name="remarks"></a>Açıklamalar
`dwFlags` [DisassemblyData yapısının üyesi olarak](../../../extensibility/debugger/reference/disassemblydata.md) kullanılır.

Bu bayraklar bit olarak birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
