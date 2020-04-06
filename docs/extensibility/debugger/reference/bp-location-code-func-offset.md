---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 32331a5b628c27dc79d6a2e5919c8d268c96a3aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738000"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Koddaki bir işlevdeki bir kesme noktasının mahsup konumunu açıklar.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Üyeler
`bstrContext`\
Kesme noktasıbağlamı, genellikle bir çağrı yığınında görüldüğü gibi bir yöntem veya işlev adı.

`pFuncPos`\
İşlevin başından itibaren işlevin adını ve göreli konumunu açıklayan [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bir birliğin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapının bir üyesidir.

Üye, `pFuncPos` işlev kesme noktasını nerede ayarladığını gösterir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
