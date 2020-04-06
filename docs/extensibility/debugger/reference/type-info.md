---
title: TYPE_INFO | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713325"
---
# <a name="type_info"></a>TYPE_INFO
Bu yapı, bir alanın türü hakkında çeşitli bilgiler belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Üyeler
 `dwKind`\
 [Birliğin](../../../extensibility/debugger/reference/dwtype-kind.md) nasıl yorumlanacağına karar veren dwTYPE_KIND numaralandırmadeğeri.

 `type.typeMeta`\
 [Yalnızca C++ ] METADATA_TYPE [bir](../../../extensibility/debugger/reference/metadata-type.md) yapı `dwKind` `TYPE_KIND_METADATA`içeriyorsa.

 `type.typePdb`\
 [Yalnızca C++ ] PDB_TYPE [bir](../../../extensibility/debugger/reference/pdb-type.md) yapı `dwKind` `TYPE_KIND_PDB`içeriyorsa.

 `type.typeBuilt`\
 [Yalnızca C++ ] BUILT_TYPE [bir](../../../extensibility/debugger/reference/built-type.md) yapı `dwKind` `TYPE_KIND_BUILT`içeriyorsa.

 `type.unused`\
 Kullanılmayan dolgu.

 `type`\
 Sendikanın adı.

 `unionmember`\
 [Yalnızca C# ] Bu, uygun yapı türüne `dwKind`göre .

## <a name="remarks"></a>Açıklamalar
 Bu yapı doldurulduğu [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) yöntemine geçirilir. Yapının içeriğinin nasıl yorumlanacağı `dwKind` alana dayanır.

> [!NOTE]
> [Yalnızca C++ ] Eşitse, `dwKind` `TYPE_KIND_BUILT`yapıyı yok ederken alttaki [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) `TYPE_INFO` nesnesini serbest bırakmak gerekir. Bu arayarak `typeInfo.type.typeBuilt.pUnderlyingField->Release()`yapılır.

 [Yalnızca C# ] Aşağıdaki tablo, üyenin `unionmember` her tür için nasıl yorumlanacağı gösterilmektedir. Örnek, bunun bir tür için nasıl yapıldığını gösterir.

|`dwKind`|`unionmember`olarak yorumlanır|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Örnek
 Bu örnek, C#'daki `unionmember` `TYPE_INFO` yapının üyesinin nasıl yorumlanacağı gösterilmektedir. Bu örnek, yalnızca bir`TYPE_KIND_METADATA`türü yorumlamayı gösterir , ancak diğerleri tam olarak aynı şekilde yorumlanır.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
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
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
