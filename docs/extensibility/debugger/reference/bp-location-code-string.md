---
description: Kullanıcının tümleşik geliştirme ortamından (IDE) girebileceği bir dizeye göre kod kesme noktaları ayarlamak için kullanılır.
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 7b29bf10ec30452465b5e8106378d48b3086f0b9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120497"
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
