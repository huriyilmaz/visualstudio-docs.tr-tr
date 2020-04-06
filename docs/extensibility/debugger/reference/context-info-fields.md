---
title: CONTEXT_INFO_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737598"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Bellek bağlamı hakkında hangi bilgilerin alıncaya kadar alınacak larını belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_CONTEXT_INFO_FIELDS {
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
`bstrModuleUrl` [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapının alanını başlatma/kullanma.

`CIF_FUNCTION`\
`CONTEXT_INFO` Yapının `bstrFunction` alanını başlatma/kullanma.

`CIF_FUNCTIONOFFSET`\
`CONTEXT_INFO` Yapının `posFunctionOffset` alanını başlatma/kullanma.

`CIF_ADDRESS`\
`CONTEXT_INFO` Yapının `bstrAddress` alanını başlatma/kullanma.

`CIF_ADDRESSOFFSET`\
`CONTEXT_INFO` Yapının `bstrAddressOffset` alanını başlatma/kullanma.

`CIF_ALLFIELDS`\
Yapının `CONTEXT_INFO` tüm alanlarını başlatma/kullanma.

## <a name="remarks"></a>Açıklamalar
Bu değerler, [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapısının hangi alanlarının başharfe atılolacağını belirtmek için [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) yöntemine bir parametre geçirilir.

Bu bayraklar, yapının hangi `CONTEXT_INFO` alanlarının kullanıldığını belirtmek için de kullanılır ve yapı döndürüldüğünde geçerlidir.

Bu değerler biraz veya birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
