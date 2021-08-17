---
description: Kesme noktası konumunu açıklamak için kullanılan yapı türünü belirtir.
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23319123066e4c78525f2fb57b07da982a8aef1763d97a66a123d44d876e2eba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434483"
---
# <a name="bp_location"></a>BP_LOCATION
Kesme noktası konumunu açıklamak için kullanılan yapı türünü belirtir.

## <a name="syntax"></a>Syntax

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
Birliğin veya [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) yorumlamak için kullanılan bir `bpLocation` değerdir. `unionmemberX`

`bpLocation`.`bplocCodeFileLine`\
[yalnızca C++ ] ise [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) yapısını `bpLocationType`  =  `BPLT_CODE_FILE_LINE` içerir.

`bpLocation.bplocCodeFuncOffset`\
[yalnızca C++ ] ise [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) yapısını `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` içerir.

`bpLocation.bplocCodeContext`\
[yalnızca C++ ] ise [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) yapısını `bpLocationType`  =  `BPLT_CODE_CONTEXT` içerir.

`bpLocation.bplocCodeString`\
[yalnızca C++ ] ise [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) yapısını `bpLocationType`  =  `BPLT_CODE_STRING` içerir.

`bpLocation.bplocCodeAddress`\
[yalnızca C++ ] ise [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) yapısını `bpLocationType`  =  `BPLT_CODE_ADDRESS` içerir.

`bpLocation.bplocDataString`\
[yalnızca C++ ] ise [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) yapısını `bpLocationType`  =  `BPLT_DATA_STRING` içerir.

`bpLocation.bplocResolution`\
[yalnızca C++ ] ise [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) yapısını `bpLocationType`  =  `BPLT_RESOLUTION` içerir.

`unionmember1`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

`unionmember2`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

`unionmember3`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

`unionmember4`\
[yalnızca C# ] Yorumlama hakkında daha fazla açıklama için bkz. Açıklamalar.

## <a name="remarks"></a>Açıklamalar
Bu yapı, BP_REQUEST_INFO [ve](../../../extensibility/debugger/reference/bp-request-info.md) [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) üyesidir.

 [yalnızca C# ] Üyeler `unionmemberX` aşağıdaki tabloya göre yorumlanır. Değerin sol sütununa bakın ve her üyenin neyi temsil ettiğini belirlemek için diğer sütunlara `bpLocationType` bakın ve uygun şekilde `unionmemberX` `unionmemberX` sıralayabilirsiniz. Bu yapının bir bölümünü C# ile yorumlamanın bir yolu için örneğine bakın.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (bağlam)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (bağlam)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (bağlam)|`string` (koşullu ifade)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (bağlam)|`string` (modül URL'si)|`string` (işlev adı)|`string` (adres)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (bağlam)|`string` (veri ifadesi)|`uint` (öğe sayısı)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Örnek
Bu örnekte, türü için `BP_LOCATION` C# içinde yapının nasıl yorumlandır olduğu `BPLT_DATA_STRING` gösterir. Bu özel tür, dört üyenin de tüm olası biçimlerde (nesne, dize ve `unionmemberX` sayı) nasıl yorumlandırılır.

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
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

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
