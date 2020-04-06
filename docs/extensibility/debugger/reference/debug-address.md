---
title: DEBUG_ADDRESS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737517"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Bu yapı bir adresi temsil eder.

## <a name="syntax"></a>Sözdizimi

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
Bu adresi içeren modülün GUID'i.

`tokClass`\
Bu adresin sınıfını veya türünü tanımlayan belirteç.

> [!NOTE]
> Bu değer bir sembol sağlayıcısına özgüdür ve bu nedenle sınıf türü için tanımlayıcı olmaktan başka genel bir anlamı yoktur.

`addr`\
Tek tek adres türlerini açıklayan yapıların birliğini içeren [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) bir yapı. Değer. `addr``dwKind` birliğin [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) nasıl yorumlanacağıADDRESS_KIND numaralandırmadan gelir.

## <a name="remarks"></a>Açıklamalar
Bu yapı doldurulmak üzere [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemine geçirilir.

**Uyarı [Yalnızca C++]**

Null `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` değeri `addr.addr.addrLocal.pLocal` değilse, belirteç işaretçisini `Release` aramanız gerekir:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
