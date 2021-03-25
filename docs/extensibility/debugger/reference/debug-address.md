---
description: Bu yapı bir adresi temsil eder.
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b250654f45f18adcfd9c52a6047b2b8798be75b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096375"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Bu yapı bir adresi temsil eder.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Üyeler
`ulAppDomainID`\
İşlem KIMLIĞI.

`guidModule`\
Bu adresi içeren modülün GUID 'SI.

`tokClass`\
Bu adresin sınıfını veya türünü tanımlayan belirteç.

> [!NOTE]
> Bu değer bir sembol sağlayıcısına özeldir ve bu nedenle, bir sınıf türü için tanımlayıcı olarak değil genel anlamı yoktur.

`addr`\
Tek tek adres türlerini açıklayan yapıların birleşimini içeren [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) yapısı. Değer `addr` .`dwKind` , birleşimin nasıl yorumlanacağını açıklayan [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmasından gelir.

## <a name="remarks"></a>Açıklamalar
Bu yapı, doldurulacak [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemine geçirilir.

**Uyarı [yalnızca C++]**

`addr.dwKind`İse `ADDRESS_KIND_METADATA_LOCAL` ve `addr.addr.addrLocal.pLocal` null bir değer değilse, `Release` belirteç işaretçisi üzerinde çağırmanız gerekir:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
