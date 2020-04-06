---
title: BPERESI_FIELDS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737757"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Kesme noktasının başarısız çözünürlüğü hakkında alınacak bilgileri belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`PERESI_BPRESLOCATION`\
`bpResLocation` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) yapının (kesme noktası çözümlemesi konumu) alanını başlatma/kullanma.

`BPERESI_PROGRAM`\
`BP_ERROR_RESOLUTION_INFO` Yapının `pProgram` alanını başlatma/kullanma.

`BPERESI_THREAD`\
`BP_ERROR_RESOLUTION_INFO` Yapının `pThread` alanını başlatma/kullanma.

`BPERESI_MESSAGE`\
`BP_ERROR_RESOLUTION_INFO` Yapının `bstrMessage` alanını başlatma/kullanma.

`BPERESI_TYPE`\
Yapının `dwType` `BP_ERROR_RESOLUTION_INFO` (kırılma noktası türü) alanını başlatma/kullanma.

`BPERESI_ALLFIELDS`\
Yapının `BP_ERROR_RESOLUTION_INFO` tüm alanlarını başlatma/kullanma.

## <a name="remarks"></a>Açıklamalar
[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) yapının hangi alanlarının başharfe atılolacağını belirtmek için [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) yöntemine parametre olarak geçirilir.

Bu değerler, `BP_ERROR_RESOLUTION_INFO` yapıdaki hangi alanların kullanıldığını belirtmek için de kullanılır ve bu yapı döndürüldüğünde geçerlidir.

Bu değerler biraz ile `OR`birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
