---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738000"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Koddaki bir işlevdeki bir kesme noktasının konum konumunu açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Üyeler
`bstrContext`\
Kesme noktası bağlamı, genellikle çağrı yığınında görülen bir yöntem veya işlev adıdır.

`pFuncPos`\
İşlevin adını ve işlevin başından ilgili göreli konumu açıklayan [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) nesnesi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bir birleşimin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısının bir üyesidir.

`pFuncPos`Üye, işlev kesme noktasının nereye ayarlanacağını gösterir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
