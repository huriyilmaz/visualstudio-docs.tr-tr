---
description: Özelliğin alt öğelerinin bir listesini alır.
title: 'IDebugProperty2:: EnumChildren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58378b04589c7e55272eeb3c2ce761516835a77c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065053"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Özelliğin alt öğelerinin bir listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
'ndaki Numaralandırılmış [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılardaki hangi alanların doldurulacağını belirten [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Numaralandırmadaki bayrakların birleşimi.

`dwRadix`\
'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak taban 'i belirtir.

`guidFilter`\
'ndaki `dwAttribFilter` `pszNameFilter` Hangi `DEBUG_PROPERTY_INFO` alt öğelerin numaralandırılacağını seçmek için ve parametreleriyle kullanılan filtrenin GUID 'si. Örneğin, `guidFilterLocals` yerel değişkenler için filtreler.

`dwAttribFilter`\
'ndaki [](../../../extensibility/debugger/reference/dbg-attrib-flags.md) `DBG_ATTRIB_METHOD` Bu özelliğin alt öğesi olabilecek tüm yöntemler için, örneğin, Numaralandırılacak nesne türlerini belirten DBG_ATTRIB_FLAGS Numaralandırmadaki bayrakların birleşimi. `guidFilter`Ve parametreleriyle birlikte kullanılır `pszNameFilter` .

`pszNameFilter`\
'ndaki `guidFilter` `dwAttribFilter` Hangi `DEBUG_PROPERTY_INFO` alt öğelerin numaralandırılacağını seçmek için ve parametreleriyle kullanılan filtrenin adı. Örneğin, bu parametre, "MyX" adlı tüm alt öğeler için "MyX" filtrelerine ayarlanıyor

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. `INFINITE`Sonsuza kadar beklemek için kullanın.

`ppEnum`\
dışı Alt özelliklerin bir listesini içeren bir [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
