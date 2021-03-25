---
description: Bu yapı, bir alanın türü hakkında çeşitli bilgi türlerini belirtir.
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b83c4a829a050b9e78b65a9a68be96d2397ea8c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070745"
---
# <a name="type_info"></a>TYPE_INFO
Bu yapı, bir alanın türü hakkında çeşitli bilgi türlerini belirtir.

## <a name="syntax"></a>Syntax

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
 [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmasından, birleşimin nasıl yorumlanacağını belirleyen bir değer.

 `type.typeMeta`\
 [Yalnızca C++] İse [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) yapısını içerir `dwKind` `TYPE_KIND_METADATA` .

 `type.typePdb`\
 [Yalnızca C++] İse [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) yapısını içerir `dwKind` `TYPE_KIND_PDB` .

 `type.typeBuilt`\
 [Yalnızca C++] İse [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) yapısını içerir `dwKind` `TYPE_KIND_BUILT` .

 `type.unused`\
 Kullanılmayan doldurma.

 `type`\
 Birleşimin adı.

 `unionmember`\
 [Yalnızca C#] Bunu temel alarak uygun yapı türüne göre sıralama `dwKind` .

## <a name="remarks"></a>Açıklamalar
 Bu yapı, doldurulduğu [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) yöntemine geçirilir. Yapının içeriğinin yorumlanması alanı temel alır `dwKind` .

> [!NOTE]
> [Yalnızca C++] `dwKind` Eşitse `TYPE_KIND_BUILT` , yapıyı yok edilirken temeldeki [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesini serbest bırakmak gereklidir `TYPE_INFO` . Bu, çağırarak yapılır `typeInfo.type.typeBuilt.pUnderlyingField->Release()` .

 [Yalnızca C#] Aşağıdaki tabloda `unionmember` her tür türü için üyenin nasıl yorumlanacağı gösterilmektedir. Örnek, bir tür türü için bunun nasıl yapıldığını gösterir.

|`dwKind`|`unionmember` yorumlanan|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Örnek
 Bu örnek, `unionmember` `TYPE_INFO` C# ' deki yapının üyesini nasıl yorumlayacağını gösterir. Bu örnek yalnızca bir türün () yorumlandığını gösterir `TYPE_KIND_METADATA` , ancak diğerleri tamamen aynı şekilde yorumlanır.

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
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
