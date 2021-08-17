---
description: Kesme noktası hata türünü belirtir.
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea1df999b285790e66c268a4d36901d149b219f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073155"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Kesme noktası hata türünü belirtir.

## <a name="syntax"></a>Syntax

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
Kesme noktası hatası olmadığını belirtir.

`BPET_TYPE_WARNING`\
Uyarı stilinde bir kesme noktası hatası belirtir.

`BPET_TYPE_ERROR`\
Hata stilinde bir kesme noktası hatası belirtir.

`BPET_SEV_HIGH`\
Yüksek önem dereceli bir kesme noktası hatası belirtir.

`BPET_SEV_GENERAL`\
Orta önem dereceli bir kesme noktası hatası belirtir.

`BPET_SEV_LOW`\
Düşük önem dereceli bir kesme noktası hatası belirtir.

`BPET_TYPE_MASK`\
Maske stili bir kesme noktası hatası belirtir.

`BPET_SEV_MASK`\
Önem derecesi maske stilinde bir kesme noktası hatası belirtir.

`BPET_GENERAL_WARNING`\
Genel uyarı stilinde bir kesme noktası hatası belirtir.

`BPET_GENERAL_ERROR`\
Genel hata stilinde bir kesme noktası hatası belirtir.

`BPET_ALL`\
Tüm kesme noktası hata türlerini belirtir.

## <a name="remarks"></a>Açıklamalar
Bu değerler bitwise ile birleştirilmiş `OR` olabilir ve veri `dwType` yapısının üyesi [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) kullanılabilir. [EnumErrorBreakpoints yöntemine parametre olarak](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) geçirildi.

Kesme noktası hata türü bir tür ve önem derecesine göre oluşur. Bu, bir kesme noktası hata türünün hiçbir zaman tek başına yalnızca bir tür (örneğin, ,) veya önem `BPET_TYPE_ERROR` derecesi (örneğin, `BPET_SEV_GENERAL` ) olduğu anlamına gelir. `BPET_GENERAL_WARNING` ve `BPET_GENERAL_ERROR` genel uyarı ve hata kesme noktaları için önceden tanımlanmış değerler sağlar.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
