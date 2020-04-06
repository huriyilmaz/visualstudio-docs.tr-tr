---
title: BP_LOCATION_DATA_STRING | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737973"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Kullanıcının tümleşik geliştirme ortamından (IDE) girebileceği bir dizeyi temel alan veri kesme noktalarını ayarlamak için kullanılır.

## <a name="syntax"></a>Sözdizimi

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
Kesme noktasının oluştuğu iş parçacığı temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`bstrContext`\
Kod içindeki kesme noktasıbağlamı, genellikle bir çağrı yığınında görüldüğü gibi bir yöntem veya işlev adı.

`bstrDataExpr`\
Kesme noktasını ayarlamak için kullanıcının girdiği veri dizesi.

`dwNumElements`\
Kesme noktasının oluştuğu veri dizesindeki öğe sayısı.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bir birliğin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapının bir üyesidir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
