---
title: BP_ERROR_TYPE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738070"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Kesme noktasının hata türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`BPET_NONE`\
Kesme noktası hatası yok.

`BPET_TYPE_WARNING`\
Uyarı stili kesme noktası hatalarını belirtir.

`BPET_TYPE_ERROR`\
Hata stili kesme noktası hatalarını belirtir.

`BPET_SEV_HIGH`\
Yüksek öneme karşı kesme noktası hatası belirtir.

`BPET_SEV_GENERAL`\
Orta önemdeki kesme noktası hatasını belirtir.

`BPET_SEV_LOW`\
Düşük öneme miklikli kesme noktası hatası belirtir.

`BPET_TYPE_MASK`\
Maske stili kesme noktası hatalarını belirtir.

`BPET_SEV_MASK`\
Önem derecesi-maske stili kesme noktası hatası belirtir.

`BPET_GENERAL_WARNING`\
Genel uyarı stili kesme noktası hatalarını belirtir.

`BPET_GENERAL_ERROR`\
Genel hata stili kesme noktası hatabelirtir.

`BPET_ALL`\
Tüm kesme noktası hata türlerini belirtir.

## <a name="remarks"></a>Açıklamalar
Bu değerler biraz ile `OR` birleştirilebilir ve `dwType` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) yapısının üyesi için kullanılabilir. [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) yöntemine parametre olarak geçirilir.

Kesme noktası hata türü bir tür ve önem açısından oluşur. Bu, kesme noktası hata türünün hiçbir zaman tek `BPET_TYPE_ERROR`başına bir tür (örneğin, `BPET_SEV_GENERAL`,) veya bir önem derecesi (örneğin) olmadığı anlamına gelir. `BPET_GENERAL_WARNING`ve `BPET_GENERAL_ERROR` genel uyarı ve hata kesme noktaları için önceden tanımlanmış değerler sağlayın.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
