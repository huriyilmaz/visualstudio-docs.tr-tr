---
title: BPRESI_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737726"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Bir kesme noktasının başarılı çözümü hakkında alınacak bilgileri belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`BPRESI_BPRESLOCATION`\
`bpResLocation` [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) yapının (kesme noktası çözümlemesi konumu) alanını başlatma/kullanma.

`BPRESI_PROGRAM`\
`BP_RESOLUTION_INFO` Yapının `pProgram` alanını başlatma/kullanma.

`BPRESI_THREAD`\
`BP_RESOLUTION_INFO` Yapının `pThread` alanını başlatma/kullanma.

`BPRESI_ALLFIELDS`\
Tüm alanları belirtir.

## <a name="remarks"></a>Açıklamalar
[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) yapısının hangi alanlarının baş harfe alıneceğini belirtmek için [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) yöntemine geçirildi.

Bu bayraklar, yapının hangi `BP_RESOLUTION_INFO` alanlarının kullanıldığını belirtmek için de kullanılır ve bu yapı döndürüldüğünde geçerlidir.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
