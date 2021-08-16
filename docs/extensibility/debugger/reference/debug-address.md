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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f4de8d07e43246a9d88a3f37a13317a41c0e5c8dad691fdecaf333ce75a81ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360852"
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
İşlem kimliği.

`guidModule`\
Bu adresi içeren modülün GUID'si.

`tokClass`\
Bu adresin sınıfını veya türünü tanımlayan belirteç.

> [!NOTE]
> Bu değer bir sembol sağlayıcısına özgüdür ve bu nedenle bir sınıf türü için tanımlayıcı dışında genel bir anlamı yoktur.

`addr`\
Tek [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) türlerini tanımlayan yapıların bir birliktelik içeren bir yapı yapısıdır. değeri. `addr``dwKind` , [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) yorumlamayı açıklayan enumerasyonundan gelir.

## <a name="remarks"></a>Açıklamalar
Bu yapı, doldurulması [için GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemine geçirildi.

**Uyarı [yalnızca C++]**

`addr.dwKind`ise `ADDRESS_KIND_METADATA_LOCAL` ve null `addr.addr.addrLocal.pLocal` değerse, belirteç işaretçisi üzerinde `Release` çağrısı gerekir:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Gereksinimler
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
