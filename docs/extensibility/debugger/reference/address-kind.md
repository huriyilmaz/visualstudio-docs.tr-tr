---
title: ADDRESS_KIND | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738154"
---
# <a name="address_kind"></a>ADDRESS_KIND
Adres türlerini belirtir.

## <a name="syntax"></a>Syntax

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
[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) yapısıyla temsil edilen yerel bir adres.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Bir `this` ( `Me` Visual Basic) işaretçisine ve [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) yapısına göre temsil edilen yönetilmeyen bir adres.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) yapısıyla temsil edilen yönetilmeyen bir fiziksel adres.

`ADDRESS_KIND_METHOD`\
[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) yapısıyla temsil edilen bir sınıf yöntemi.

`ADDRESS_KIND_FIELD`\
[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) yapısıyla temsil edilen bir sınıf alanı.

`ADDRESS_KIND_LOCAL`\
Adres yerel bir değişken için ve [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) yapısıyla temsil edilir.

`ADDRESS_KIND_PARAM`\
[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) yapısıyla temsil edilen bir yöntem veya işlev parametresi.

`ADDRESS_KIND_ARRAYELEM`\
[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) yapısıyla temsil edilen bir dizi öğesi.

`ADDRESS_KIND_RETVAL`\
[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) yapısıyla temsil edilen bir dönüş değeri.

## <a name="remarks"></a>Açıklamalar
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemi olası yapıların birleşimini içeren [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısını döndürür, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) yapısı. `dwKind` `DEBUG_ADDRESS_UNION` Yapının alanı `ADDRESS_KIND` değeri tutar ve birleşim alanının nasıl yorumlanacağını açıklar.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: SH. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
