---
title: DEBUG_ADDRESS_UNION | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737530"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Farklı türde adresleri açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Üyeler
`dwKind`\
ADDRESS_KIND numaralandırmadan birliğin nasıl yorumlanacağına göre bir değer. [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

`addr.addrNative`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_NATIVE [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) yapısını içerir.

`addr.addrThisRel`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) yapısını içerir.

`addr.addUPhysical`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) yapısını içerir.

`addr.addrMethod`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_METHOD[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) yapısını içerir.

`addr.addrField`\
[Yalnızca C++ ] eğer `dwKind` = ADDRESS_KIND_FIELD[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) yapısını içerir.

`addr.addrLocal`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_LOCAL[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) yapısını içerir.

`addr.addrParam`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_PARAM[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) yapısını içerir.

`addr.addrArrayElem`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_ARRAYELEM[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) yapısını içerir.

`addr.addrRetVal`\
[Yalnızca C++ ] if `dwKind` = ADDRESS_KIND_RETVAL[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) yapısını içerir.

`addr.unused`\
[Yalnızca C++ dolgu.

`addr`\
[Yalnızca C++ ] Sendikanın adı.

`unionmember`\
[Yalnızca C# ] Bu değerin `dwKind`uygun yapı türüne göre marshaled gerekir. Bkz. Birliğin `dwKind` ilişkisi ve yorumu için açıklamalar.

## <a name="remarks"></a>Açıklamalar
Bu yapı [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısının bir parçasıdır ve farklı türde adreslerden `DEBUG_ADDRESS` birini temsil eder (yapı [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemine yapılan bir çağrı yla doldurulur).

 [Yalnızca C# ] Aşağıdaki tablo, üyenin `unionmember` her bir adres türü için nasıl yorumlanacağı gösterilmektedir. Örnek, bunun bir tür adres için nasıl yapıldığını gösterir.

|`dwKind`|`unionmember`olarak yorumlanır|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Örnek
Bu örnek, C#'daki yapının bir tür adresinin ()`METADATA_ADDRESS_ARRAYELEM`nasıl yorumlanacağıgöster. `DEBUG_ADDRESS_UNION` Kalan öğeler tam olarak aynı şekilde yorumlanabilir.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: sh.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
