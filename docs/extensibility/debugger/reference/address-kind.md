---
title: ADDRESS_KIND | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738154"
---
# <a name="address_kind"></a>ADDRESS_KIND
Adres türlerini belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Alanlar
`ADDRESS_KIND_NATIVE`\
[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) yapısı yla temsil edilen yerel bir adres.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Bir `this` (Visual`Me` Basic'te) işaretçisine göre yönetilmeyen bir adres ve [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) yapısı tarafından temsil edilir.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
UNMANAGED_ADDRESS_PHYSICAL yapısı tarafından temsil edilen yönetilmeyen [bir](../../../extensibility/debugger/reference/unmanaged-address-physical.md) fiziksel adres.

`ADDRESS_KIND_METHOD`\
[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) yapısı yla temsil edilen bir sınıf yöntemi.

`ADDRESS_KIND_FIELD`\
[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) yapısıyla temsil edilen bir sınıfın alanı.

`ADDRESS_KIND_LOCAL`\
Adres yerel bir değişken içindir ve [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) yapısı tarafından temsil edilir.

`ADDRESS_KIND_PARAM`\
[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) yapısı tarafından temsil edilen bir yöntem veya işlev parametresi.

`ADDRESS_KIND_ARRAYELEM`\
METADATA_ADDRESS_ARRAYELEM yapısı yla temsil edilen [bir](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) dizi öğesi.

`ADDRESS_KIND_RETVAL`\
[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) yapısı tarafından temsil edilen bir iade değeri.

## <a name="remarks"></a>Açıklamalar
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemi, olası yapıların birleşimini, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) yapıyı içeren [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapıyı döndürür. `DEBUG_ADDRESS_UNION` Yapıalanı `dwKind` `ADDRESS_KIND` değeri tutar ve birleşim alanının nasıl yorumlanacağı açıklanır.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
