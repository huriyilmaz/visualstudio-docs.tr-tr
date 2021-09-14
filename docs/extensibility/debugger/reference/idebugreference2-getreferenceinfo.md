---
description: Başvuru DEBUG_REFERENCE_INFO yapıyı alır.
title: IDebugReference2::GetReferenceInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88dc8d4bdbc0e354ccc327aa0c5b6968091c19c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634825"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Bir [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) açıklayan bir veri yapısı alır. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
[in] Veri verisi [yapısında doldurulacak](../../../extensibility/debugger/reference/debugref-info-flags.md) alanları belirleyen DEBUGREF_INFO_FLAGS bir bayrak [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)

`nRadix`\
[in] Herhangi bir sayısal bilgiyi biçimlendirmek için kullanılacak radyan.

`dwTimeout`\
[in] Bu yöntemden dönmeden önce bek süresi (milisaniye cinsinden). Süresiz `INFINITE` olarak beklemek için kullanın.

`rgpArgs`\
[in] [IDebugReference2 nesneleri dizisi.](../../../extensibility/debugger/reference/idebugreference2.md) Gelecekteki kullanım için ayrılmıştır; null değere ayarlanır.

`dwArgCount`\
[in] Dizideki başvuru bağımsız `rgpArgs` değişkenlerinin sayısı. Gelecekteki kullanım için ayrılmıştır; 0 olarak ayarlayın.

`pReferenceInfo`\
[out] Özelliğin [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) doldurulan bir yapıdır.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
