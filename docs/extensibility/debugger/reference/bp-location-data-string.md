---
description: Kullanıcının tümleşik geliştirme ortamından (IDE) girebileceği bir dizeyi temel alan veri kesme noktaları ayarlamak için kullanılır.
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 37495719a5590fff6dc2ec61cb863e2163f468c7ccf15e316a034cb510c4f0a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239340"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Kullanıcının tümleşik geliştirme ortamından (IDE) girebileceği bir dizeyi temel alan veri kesme noktaları ayarlamak için kullanılır.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Üyeler
`pThread`\
Kesme noktasının gerçekleştiği iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`bstrContext`\
Bir çağrı yığınında görülen, genellikle bir yöntem veya işlev adı içindeki kesme noktasının bağlamı.

`bstrDataExpr`\
Kullanıcının kesme noktasını ayarlamak için girdiği veri dizesi.

`dwNumElements`\
Kesme noktasının gerçekleştiği veri dizesindeki öğe sayısı.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bir birleşimin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısının bir üyesidir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
