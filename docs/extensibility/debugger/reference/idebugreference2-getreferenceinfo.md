---
description: Bir başvuruyu açıklayan DEBUG_REFERENCE_INFO yapısını alır.
title: 'IDebugReference2:: Getreferenceınfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef953ccde844ac7a2fb5289affaf381f56af8719
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168930"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Bir başvuruyu açıklayan [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısını alır. Daha sonraki kullanımlar için ayrılmıştır.

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
'ndaki [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısında doldurulacak alanları belirleme [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) numaralandırmasındaki bayrakların birleşimi.

`nRadix`\
'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak taban tabanı.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süre (milisaniye cinsinden). `INFINITE`Sonsuza kadar beklemek için kullanın.

`rgpArgs`\
'ndaki [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnelerinden oluşan bir dizi. Gelecekte kullanılmak üzere ayrılmıştır; null değere ayarlayın.

`dwArgCount`\
'ndaki Dizideki başvuru bağımsız değişkenlerinin sayısı `rgpArgs` . Gelecekte kullanılmak üzere ayrılmıştır; 0 olarak ayarlayın.

`pReferenceInfo`\
dışı Özelliğin açıklamasıyla doldurulmuş [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
