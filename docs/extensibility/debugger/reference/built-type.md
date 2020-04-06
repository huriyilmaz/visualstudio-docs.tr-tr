---
title: BUILT_TYPE | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737702"
---
# <a name="built_type"></a>BUILT_TYPE
Bu yapı, meta verilerden alınan bir alan türü hakkında bilgi belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Üyeler
`ulAppDomainID`\
Sembolün geldiği uygulamanın kimliği. Bu, uygulamanın bir örneğini benzersiz olarak tanımlamak için kullanılır.

`guidModule`\
Bu alanı içeren modülün GUID'i.

`pUnderlyingField`\
Bu yapılı alanla ilişkili temel alanı tanımlayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, `dwKind` `TYPE_INFO` yapıalanı ayarlandığında `TYPE_KIND_BUILT` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) yapısında birliğin bir parçası olarak görünür [(dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmadan bir değer).

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
