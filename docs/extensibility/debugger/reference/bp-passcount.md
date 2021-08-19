---
description: Koşullu kesme noktasının tetikleneceği sayı ve koşulları açıklar.
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd670e24fc10c2df445a66c5112e8c8d10eac79a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120432"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Koşullu kesme noktasının tetikleneceği sayı ve koşulları açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Üyeler
`dwPassCount`\
Başlamadan önce kesme noktasının kaç kez geçmesi gerektiği.

`stylePassCount`\
Kesme noktası geçiş sayısının stilini belirten [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) numaralandırmasından bir değer.

## <a name="remarks"></a>Açıklamalar
Bu yapı [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yapısının bir üyesidir.

Bu yapı ayrıca[setpasscount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) ve[setpasscount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) yöntemlerine bir parametre olarak geçirilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
