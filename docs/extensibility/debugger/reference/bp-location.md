---
description: Kesme noktasının konumunu anlatmak için kullanılan yapının türünü belirtir.
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ee3c9246c25517c2b0bc095c4035400e43d29b5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096726"
---
# <a name="bp_location"></a>BP_LOCATION
Kesme noktasının konumunu anlatmak için kullanılan yapının türünü belirtir.

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
Birleşim veya üyeleri yorumlamak için kullanılan [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) numaralandırmasından bir değer `bpLocation` `unionmemberX` .

`bpLocation`.`bplocCodeFileLine`\
[Yalnızca C++] İse [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) yapısını içerir `bpLocationType`  =  `BPLT_CODE_FILE_LINE` .

`bpLocation.bplocCodeFuncOffset`\
[Yalnızca C++] İse [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) yapısını içerir `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` .

`bpLocation.bplocCodeContext`\
[Yalnızca C++] İse [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) yapısını içerir `bpLocationType`  =  `BPLT_CODE_CONTEXT` .

`bpLocation.bplocCodeString`\
[Yalnızca C++] İse [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) yapısını içerir `bpLocationType`  =  `BPLT_CODE_STRING` .

`bpLocation.bplocCodeAddress`\
[Yalnızca C++] İse [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) yapısını içerir `bpLocationType`  =  `BPLT_CODE_ADDRESS` .

`bpLocation.bplocDataString`\
[Yalnızca C++] İse [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) yapısını içerir `bpLocationType`  =  `BPLT_DATA_STRING` .

`bpLocation.bplocResolution`\
[Yalnızca C++] İse [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) yapısını içerir `bpLocationType`  =  `BPLT_RESOLUTION` .

`unionmember1`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

`unionmember2`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

`unionmember3`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

`unionmember4`\
[Yalnızca C#] Yorumlama hakkında açıklamalar bölümüne bakın.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapılarının bir üyesidir.

 [Yalnızca C#] `unionmemberX` Üyeler aşağıdaki tabloya göre yorumlanır. Değerin sol sütununu arayın `bpLocationType` ve ardından her üyenin ne kadar temsil ettiğini belirlemek için diğer sütunlara bakın `unionmemberX` `unionmemberX` . C# ' de bu yapının bir parçasını yorumlamak için bir yol örneğine bakın.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (bir bağlam)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (bir bağlam)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (bir bağlam)|`string` (koşullu ifade)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (bir bağlam)|`string` (modül URL 'SI)|`string` (işlev adı)|`string` adrestir|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (bir bağlam)|`string` (veri ifadesi)|`uint` (öğe sayısı)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Örnek
Bu örnek `BP_LOCATION` , türü Için C# ' deki yapının nasıl yorumlanacağı gösterilmektedir `BPLT_DATA_STRING` . Bu belirli tür `unionmemberX` , tüm olası biçimlerdeki dört üyenin (nesne, dize ve sayı) nasıl yorumlanacağı gösterilmektedir.

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
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

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
