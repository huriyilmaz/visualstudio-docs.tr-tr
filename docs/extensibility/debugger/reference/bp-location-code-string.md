---
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 0fc0d9a053faf69fde500333ab0faafa0e8d3448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737987"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Kullanıcının tümleşik geliştirme ortamından (IDE) girebileceği bir dizeye göre kod kesme noktaları ayarlamak için kullanılır.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Üyeler
`bstrContext`\
Bir çağrı yığınında görülen, genellikle bir yöntem veya işlev adı içindeki kesme noktasının bağlamı.

`bstrCodeExpr`\
Kullanıcının kod kesme noktasını tanımlamakta kullandığı dize.

## <a name="remarks"></a>Açıklamalar
Bu yapı, bir birleşimin parçası olarak [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısının bir üyesidir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar ve Birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
