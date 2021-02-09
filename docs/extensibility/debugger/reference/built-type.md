---
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35ae5661127c0e19e87c96a47a2985161beae7c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874388"
---
# <a name="built_type"></a>BUILT_TYPE
Bu yapı, meta verilerden alınan bir alan türü hakkında bilgi belirtir.

## <a name="syntax"></a>Syntax

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
Simgenin geldiği uygulamanın KIMLIĞI. Bu, uygulamanın bir örneğini benzersiz bir şekilde tanımlamak için kullanılır.

`guidModule`\
Bu alanı içeren modülün GUID 'ı.

`pUnderlyingField`\
Bu yerleşik alanla ilişkili temel alanı tanımlayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [](../../../extensibility/debugger/reference/type-info.md) `dwKind` `TYPE_INFO` yapı alanı `TYPE_KIND_BUILT` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmasından bir değer) olarak ayarlandığında TYPE_INFO yapısındaki birleşimin bir parçası olarak görüntülenir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
