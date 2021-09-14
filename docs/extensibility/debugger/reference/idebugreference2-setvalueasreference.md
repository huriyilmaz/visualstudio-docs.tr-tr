---
description: Başka bir başvurudan başvuru değerini ayarlar.
title: IDebugReference2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48030e2314764767b049502ce081a2711a00111b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126727005"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Başka bir başvurudan başvuru değerini ayarlar. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametreler
`rgpArgs`\
[in] Başvuru değerini [ayarlamayı belirlemek için kullanılan IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesneleri dizisi.

`dwArgCount`\
[in] Dizideki başvuru sayısı.

`pValue`\
[in] Özellik [değerinin ayarlandırı bir IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi.

`dwTimeout`\
[in] Bu yöntemden dönmeden önce bek süresi (milisaniye cinsinden). Süresiz `INFINITE` olarak beklemek için kullanın.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
