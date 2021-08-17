---
description: Farklı türlerde adresleri açıklar.
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab8f7b268f347380284662b2ef35dab03e99513f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073129"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Farklı türlerde adresleri açıklar.

## <a name="syntax"></a>Syntax

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
Bir ADDRESS_KIND [](../../../extensibility/debugger/reference/address-kind.md) belirten bir değer.

`addr.addrNative`\
[yalnızca C++ ] if = [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) `dwKind` yapıyı ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[yalnızca C++ ] =[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) bir UNMANAGED_ADDRESS_THIS_RELATIVE `dwKind` yapısını ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[yalnızca C++ ] =[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) bir UNMANAGED_ADDRESS_PHYSICAL `dwKind` yapısını ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[yalnızca C++ ] =[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) bir `dwKind` ADDRESS_KIND_METHOD.

`addr.addrField`\
[yalnızca C++ ] if =[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) `dwKind` yapıyı ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[yalnızca C++ ] if =[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) `dwKind` yapıyı ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[yalnızca C++ ] =[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) bir METADATA_ADDRESS_PARAM `dwKind` yapısını ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[yalnızca C++ ] if =[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) `dwKind` yapıyı ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[yalnızca C++ ] =[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) yapısını `dwKind` ADDRESS_KIND_RETVAL.

`addr.unused`\
[Yalnızca C++ ] doldurma.

`addr`\
[yalnızca C++ ] Birliğin adı.

`unionmember`\
[yalnızca C# ] Bu değerin, temel alarak uygun yapı türüne sıra olması `dwKind` gerekir. Arasındaki ilişki ve birlikteliğin yorumu `dwKind` için bkz. Açıklamalar.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısının bir parçası ve farklı türde adreslerden birini temsil eder (yapı `DEBUG_ADDRESS` [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) yöntemine yapılan bir çağrıyla doldurulur).

 [yalnızca C# ] Aşağıdaki tabloda, her bir adres için `unionmember` üyenin nasıl yorumlanması gerekir? Örnek, bunun tek bir adres için nasıl olduğunu gösterir.

|`dwKind`|`unionmember` olarak yorumlanır|
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
Bu örnekte, C# içinde yapının bir tür adresinin ( `METADATA_ADDRESS_ARRAYELEM` ) `DEBUG_ADDRESS_UNION` nasıl yorumlandırılması gösterir. Kalan öğeler tam olarak aynı şekilde yorumlanır.

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
Üst bilgi: sh.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
