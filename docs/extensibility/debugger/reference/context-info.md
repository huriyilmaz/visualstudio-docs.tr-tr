---
title: CONTEXT_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737572"
---
# <a name="context_info"></a>CONTEXT_INFO
Bu yapı, bellek bağlamı veya kod bağlamı açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Üyeler
`dwFields`\
Hangi alanların doldurulacağını belirten numaralandırma [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) gelen bayrakların<strong>birleşimi.</strong>

`bstrModuleUrl`\
Bağlamın bulunduğu modülün adı.

`bstrFunction`\
Bağlamın bulunduğu işlev adı.

`posFunctionOffset`\
Kod bağlamıyla ilişkili işlevin satır ve sütun mahsupunu tanımlayan [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) bir yapı.

`bstrAddress`\
Verilen bağlamın bulunduğu koddaki adres.

`bstrAddressOffset`\
Verilen bağlamın bulunduğu koddaki adresin mahsup edilir.

`bstrAddressAbsolute`\
Verilen bağlamın bulunduğu bellekteki mutlak adres.

## <a name="remarks"></a>Açıklamalar
Bu yapı [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) yöntemine yapılan bir çağrıdan döndürülür.

Bu yapı için tipik **bir** kullanım bellek hata ayıklama penceresi desteklenir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
