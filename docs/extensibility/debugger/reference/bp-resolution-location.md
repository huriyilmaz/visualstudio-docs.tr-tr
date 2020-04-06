---
title: BP_RESOLUTION_LOCATION | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737817"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Kesme noktası çözümlü konumuyapısını belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Üyeler
`bpType`\
Sendika veya `unionmemberX` üyelerin nasıl yorumlanacağına BP_TYPE numaralandırma değeri. [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) `bpResLocation`

`bpResLocation.bpresCode`\
[Yalnızca C++ ] Eğer [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) yapısını `bpType`  =  `BPT_CODE`içerir.

`bpResLocation.bpresData`\
[Yalnızca C++ ] [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) yapısını içerir. `bpType`  =  `BPT_DATA`

`bpResLocation.unused`\
[Yalnızca C++ ] Yer tutucu.

`unionmember1`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

`unionmember2`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

`unionmember3`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

`unionmember4`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

## <a name="remarks"></a>Açıklamalar
Bu yapı [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) ve [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) yapıların bir üyesidir.

 [Yalnızca C# ] Üyeler `unionmemberX` aşağıdaki tabloya göre yorumlanır. Her `bpType` `unionmemberX` üyenin neyi temsil edip buna `unionmemberX` göre mareşallik yaptığını belirlemek için sol sütuna bakın. Bu yapıyı C#'da yorumlamanın bir yolu için Örnek'e bakın.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(veri ifade)|`string`(işlev adı)|`string`(resim adı)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Örnek
Bu örnek, C#'daki yapının nasıl yorumlanacağı gösterilmektedir. `BP_RESOLUTION_LOCATION`

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
