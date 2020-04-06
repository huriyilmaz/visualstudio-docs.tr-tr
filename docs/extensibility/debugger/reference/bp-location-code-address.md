---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: c215630e522adabdbd285e00d4bcd87cae22a931
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738030"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
Koddaki bir adresteki kesme noktasının konumunu açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Üyeler
`bstrContext`\
Kesme noktasıbağlamı, genellikle bir çağrı yığınında görüldüğü gibi bir yöntem veya işlev adı.

`bstrModuleUrl`\
Kesme noktasını içeren modülün URL'si.

`bstrFunction`\
Kesme noktasını içeren işlevin adı.

`bstrAddress`\
Bir ifade değerlendiricisi tarafından ayrıştırılan kesme noktasının adresi, onu bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesine bağlamak için.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bir birliğin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapının bir üyesidir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
