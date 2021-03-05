---
description: Koddaki bir adresteki bir kesme noktasının konumunu açıklar.
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 961a62284b841d56ae73a29df0e83810ff9d7d20
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144448"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
Koddaki bir adresteki bir kesme noktasının konumunu açıklar.

## <a name="syntax"></a>Syntax

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
Kesme noktası bağlamı, genellikle çağrı yığınında görülen bir yöntem veya işlev adıdır.

`bstrModuleUrl`\
Kesme noktasını içeren modülün URL 'SI.

`bstrFunction`\
Kesme noktasını içeren işlevin adı.

`bstrAddress`\
Bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesine bağlamak için bir ifade değerlendirici tarafından ayrıştırılmış kesme noktasının adresi.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bir birleşimin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısının bir üyesidir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
