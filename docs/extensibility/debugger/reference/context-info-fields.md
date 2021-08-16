---
description: Bir bellek bağlamı hakkında hangi bilgilerin alın başkanı olduğunu belirtir.
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95ca1e9e65a1fac9a9171bed1bfef90b011c44a1308f2a6eb01b9a029d1acbc3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360904"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Bir bellek bağlamı hakkında hangi bilgilerin alın başkanı olduğunu belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Alanlar
`CIF_MODULEURL`\
İlke `bstrModuleUrl` yapısının alanını [CONTEXT_INFO.](../../../extensibility/debugger/reference/context-info.md)

`CIF_FUNCTION`\
Yapı alanını `bstrFunction` `CONTEXT_INFO` başlatma/kullanma.

`CIF_FUNCTIONOFFSET`\
Yapı alanını `posFunctionOffset` `CONTEXT_INFO` başlatma/kullanma.

`CIF_ADDRESS`\
Yapı alanını `bstrAddress` `CONTEXT_INFO` başlatma/kullanma.

`CIF_ADDRESSOFFSET`\
Yapı alanını `bstrAddressOffset` `CONTEXT_INFO` başlatma/kullanma.

`CIF_ALLFIELDS`\
Yapının tüm alanlarını `CONTEXT_INFO` başlat/kullan.

## <a name="remarks"></a>Açıklamalar
Bu değerler, CONTEXT_INFO yapısının hangi alanlarının başlat olacağını [belirtmek için](../../../extensibility/debugger/reference/context-info.md) [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) yöntemine bir parametre geçirildi.

Bu bayraklar yapının hangi alanlarının kullanıldığı `CONTEXT_INFO` ve yapı döndürülürken geçerli olduğunu belirtmek için de kullanılır.

Bu değerler bitwise OR ile birleştirilmiş olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
