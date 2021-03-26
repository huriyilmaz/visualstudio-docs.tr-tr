---
description: Kesme noktası çözümleme konumunun yapısını belirtir.
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aefbb27a7eb693ceef3bd64afb610607697ac23e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089127"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Kesme noktası çözümleme konumunun yapısını belirtir.

## <a name="syntax"></a>Syntax

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
Birleşim veya üyelerin nasıl yorumlanacağını belirten [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) numaralandırmasından bir değer `bpResLocation` `unionmemberX` .

`bpResLocation.bpresCode`\
[Yalnızca C++] İse [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) yapısını içerir `bpType`  =  `BPT_CODE` .

`bpResLocation.bpresData`\
[Yalnızca C++] İse [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) yapısını içerir `bpType`  =  `BPT_DATA` .

`bpResLocation.unused`\
[Yalnızca C++] Yer tutucu.

`unionmember1`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

`unionmember2`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

`unionmember3`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

`unionmember4`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) ve [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) yapılarının bir üyesidir.

 [Yalnızca C#] `unionmemberX` Üyeler aşağıdaki tabloya göre yorumlanır. `bpType`Her üyenin ne kadar `unionmemberX` temsil ettiğini ve ne kadar uygun olduğunu belirlemek için, bu değerin içindeki sol sütuna bakın `unionmemberX` . C# dilinde bu yapıyı yorumlamak için bir yol örneğine bakın.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (veri ifadesi)|`string` (işlev adı)|`string` (görüntü adı)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Örnek
Bu örnekte, `BP_RESOLUTION_LOCATION` C# ' de yapının nasıl yorumlanacağı gösterilmektedir.

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
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
