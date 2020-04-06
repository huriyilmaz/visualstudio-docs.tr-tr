---
title: IDebugReference2::SetValueAsReference | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4767dbe08e716d64ea03c18a1c4a6f7d6690a7b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720301"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Başka bir başvurudan başvurudeğerini ayarlar. Daha sonraki kullanımlar için ayrılmıştır.

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
[içinde] Başvuru değerinin nasıl ayarlanabildiğini belirlemek için kullanılan Bir Dizi [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi.

`dwArgCount`\
[içinde] Dizideki başvuru sayısı.

`pValue`\
[içinde] Özellik değerini ayarlamak için bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden maksimum süre. Süresiz beklemek için kullanın. `INFINITE`

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
