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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b433f7b58753408c916074539d9d0b6275d1ce17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145828"
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
Bir BP_TYPE [veya](../../../extensibility/debugger/reference/bp-type.md) üyeleri yorumlamayı belirten bir `bpResLocation` `unionmemberX` değer.

`bpResLocation.bpresCode`\
[yalnızca C++ ] ise [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) yapısını `bpType`  =  `BPT_CODE` içerir.

`bpResLocation.bpresData`\
[yalnızca C++ ] ise [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) yapısını `bpType`  =  `BPT_DATA` içerir.

`bpResLocation.unused`\
[yalnızca C++ ] Yer tutucu.

`unionmember1`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

`unionmember2`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

`unionmember3`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

`unionmember4`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

## <a name="remarks"></a>Açıklamalar
Bu yapı, BP_ERROR_RESOLUTION_INFO [ve](../../../extensibility/debugger/reference/bp-error-resolution-info.md) [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) üyesidir.

 [yalnızca C# ] Üyeler `unionmemberX` aşağıdaki tabloya göre yorumlanır. Her üyenin neyi temsil ettiğini belirlemek ve uygun şekilde sıralamak için değerin sol sütununa ve sonra `bpType` `unionmemberX` `unionmemberX` genelindeki sütununa bakın. Bu yapıyı C# ile yorumlamanın bir yolu için Bkz. Örnek.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (veri ifadesi)|`string` (işlev adı)|`string` (görüntü adı)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Örnek
Bu `BP_RESOLUTION_LOCATION` örnekte, C# içinde yapının nasıl yorumlandır olduğu gösterir.

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
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
