---
description: Bir kesme noktasının tetiklendiği koşulları açıklar.
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 560cf7184e5fa7b25e35410313535675713742aa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085344"
---
# <a name="bp_condition"></a>BP_CONDITION
Bir kesme noktasının tetiklendiği koşulları açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Üyeler
`pThread`\
Kesme noktasını içeren uygulama için etkin iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`styleCondition`\
Bu kesme noktası koşulunun stilini açıklayan [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) numaralandırmasından bir değer.

`bstrContext`\
Kesme noktasının konumu.

`bstrCondition`\
Kesme noktasının Tetikleme koşulu.

`nRadix`\
Herhangi bir sayısal bilgiyi değerlendirmek için kullanılan Radix.

## <a name="remarks"></a>Açıklamalar
Bu yapı, [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapılarının bir üyesidir.

Bu yapı ayrıca [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) ve [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) yöntemlerine bir parametre olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
