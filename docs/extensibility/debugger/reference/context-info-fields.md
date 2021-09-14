---
description: Bellek bağlamı hakkında hangi bilgilerin alınması gerektiğini belirtir.
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
ms.openlocfilehash: 36adf58598248bb6e59045e80b185dd2684b64b7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725305"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Bellek bağlamı hakkında hangi bilgilerin alınması gerektiğini belirtir.

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
`bstrModuleUrl` [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapısının alanını başlatın/kullanın.

`CIF_FUNCTION`\
Yapının alanını başlatın/kullanın `bstrFunction` `CONTEXT_INFO` .

`CIF_FUNCTIONOFFSET`\
Yapının alanını başlatın/kullanın `posFunctionOffset` `CONTEXT_INFO` .

`CIF_ADDRESS`\
Yapının alanını başlatın/kullanın `bstrAddress` `CONTEXT_INFO` .

`CIF_ADDRESSOFFSET`\
Yapının alanını başlatın/kullanın `bstrAddressOffset` `CONTEXT_INFO` .

`CIF_ALLFIELDS`\
Yapının tüm alanlarını başlatın/kullanın `CONTEXT_INFO` .

## <a name="remarks"></a>Açıklamalar
Bu değerler, [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) yapısının hangi alanlarının başlatıldığını göstermek Için [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) yöntemine bir parametre geçirilir.

Bu bayraklar aynı zamanda yapının hangi alanlarının `CONTEXT_INFO` kullanıldığını ve yapı döndürüldüğünde geçerli olduğunu göstermek için de kullanılır.

Bu değerler, bit düzeyinde veya ile birleştirilebilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
