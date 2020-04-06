---
title: BP_LOCATION | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737937"
---
# <a name="bp_location"></a>BP_LOCATION
Kesme noktasının konumunu açıklamak için kullanılan yapı türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Üyeler
`bpLocationType`\
Sendikayı veya `unionmemberX` üyeleri yorumlamak için kullanılan BP_LOCATION_TYPE numaralandırmadeğeri. [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) `bpLocation`

`bpLocation`.`bplocCodeFileLine`\
[Yalnızca C++ ] [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) yapısını içerir. `bpLocationType`  =  `BPLT_CODE_FILE_LINE`

`bpLocation.bplocCodeFuncOffset`\
[Yalnızca C++ ] [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) yapısını içerir. `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`

`bpLocation.bplocCodeContext`\
[Yalnızca C++ ] Eğer [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) yapısını `bpLocationType`  =  `BPLT_CODE_CONTEXT`içerir.

`bpLocation.bplocCodeString`\
[Yalnızca C++ ] Eğer [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) yapısını `bpLocationType`  =  `BPLT_CODE_STRING`içerir.

`bpLocation.bplocCodeAddress`\
[Yalnızca C++ ] Eğer [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) yapısını `bpLocationType`  =  `BPLT_CODE_ADDRESS`içerir.

`bpLocation.bplocDataString`\
[Yalnızca C++ ] [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) yapısını içerir. `bpLocationType`  =  `BPLT_DATA_STRING`

`bpLocation.bplocResolution`\
[Yalnızca C++ ] Eğer [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) yapısını `bpLocationType`  =  `BPLT_RESOLUTION`içerir.

`unionmember1`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

`unionmember2`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

`unionmember3`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

`unionmember4`\
[Yalnızca C# ] Nasıl yorumlanacağına ilişkin Açıklamalar'a bakın.

## <a name="remarks"></a>Açıklamalar
Bu yapı [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapıların bir üyesidir.

 [Yalnızca C# ] Üyeler `unionmemberX` aşağıdaki tabloya göre yorumlanır. Değer için sol sütuna `bpLocationType` bakın ve her `unionmemberX` üyenin neyi temsil etmesini `unionmemberX` belirlemek için diğer sütunlara bakın ve buna göre mareşallik edin. Bu yapının bir bölümünü C#'da yorumlamanın bir yolu için örneğe bakın.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(bir bağlam)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(bir bağlam)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(bir bağlam)|`string`(koşullu ifade)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(bir bağlam)|`string`(modül URL'si)|`string`(işlev adı)|`string`(adres)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(bir bağlam)|`string`(veri ifade)|`uint`(eleman sayısı)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Örnek
Bu örnek, C# `BP_LOCATION` yapısının türü `BPLT_DATA_STRING` için nasıl yorumlanacağı gösterilmektedir. Bu tür, dört `unionmemberX` üyenin tüm olası biçimlerde (nesne, dize ve sayı) nasıl yorumlanacağımı gösterir.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
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
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
