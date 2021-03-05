---
description: Bir kesme noktasının hata türünü belirtir.
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ced08f5bf4cd51a1f89f139fd19971e21e2225e6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144435"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Bir kesme noktasının hata türünü belirtir.

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
Bir uyarı stili kesme noktası hatası belirtir.

`BPET_TYPE_ERROR`\
Bir hata stili kesme noktası hatası belirtir.

`BPET_SEV_HIGH`\
Yüksek öneme sahip kesme noktası hatasını belirtir.

`BPET_SEV_GENERAL`\
Orta öneme sahip kesme noktası hatasını belirtir.

`BPET_SEV_LOW`\
Düşük öneme sahip kesme noktası hatasını belirtir.

`BPET_TYPE_MASK`\
Bir maske stili kesme noktası hatası belirtir.

`BPET_SEV_MASK`\
Bir önem düzeyi-maske stili kesme noktası hatası belirtir.

`BPET_GENERAL_WARNING`\
Genel uyarı stili kesme noktası hatasını belirtir.

`BPET_GENERAL_ERROR`\
Genel hata stili kesme noktası hatasını belirtir.

`BPET_ALL`\
Tüm kesme noktası hata türlerini belirtir.

## <a name="remarks"></a>Açıklamalar
Bu değerler bit düzeyinde birleştirilebilir `OR` ve `dwType` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) yapısının üyesi için kullanılabilir. [Enumerrorkesmenoktaları](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) metoduna parametre olarak geçirilir.

Kesme noktası hata türü bir tür ve önem derecesi oluşur. Bu, kesme noktası hata türünün hiçbir şekilde bir tür (örneğin, `BPET_TYPE_ERROR` ) veya önem derecesi (örneğin,) olduğu anlamına gelir `BPET_SEV_GENERAL` . `BPET_GENERAL_WARNING` ve `BPET_GENERAL_ERROR` genel uyarı ve hata kesme noktaları için önceden tanımlanmış değerler sağlar.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
