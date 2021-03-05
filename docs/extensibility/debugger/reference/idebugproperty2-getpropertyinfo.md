---
description: Bir özelliği tanımlayan DEBUG_PROPERTY_INFO yapısını alır.
title: 'IDebugProperty2:: GetPropertyInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: deb8dbe5b055f42f21c087dcb2cc7a14e16858f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166793"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Bir özelliği tanımlayan [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPropertyInfo ( 
   DEBUGPROP_INFO_FLAGS dwFields,
   DWORD                nRadix,
   DWORD                dwTimeout,
   IDebugReference2**   rgpArgs,
   DWORD                dwArgCount,
   DEBUG_PROPERTY_INFO* pPropertyInfo
);
```

```cpp
int GetPropertyInfo ( 
   enum_DEBUGPROP_INFO_FLAGS dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_PROPERTY_INFO[]     pPropertyInfo
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
'ndaki Yapıda doldurulacak alanları belirten [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Numaralandırmadaki değerlerin bir birleşimi `pPropertyInfo` .

`nRadix`\
'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak Radix.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. `INFINITE`Sonsuza kadar beklemek için kullanın.

`rgpArgs`\
[in, out] Gelecekte kullanılmak üzere ayrılmıştır; null değere ayarlayın.

`dwArgCount`\
'ndaki Gelecekte kullanılmak üzere ayrılmıştır; sıfır olarak ayarlayın.

`pPropertyInfo`\
dışı Özelliğin açıklamasıyla doldurulmuş bir [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
