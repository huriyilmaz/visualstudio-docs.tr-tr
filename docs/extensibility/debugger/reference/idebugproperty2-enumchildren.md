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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a377ea09822db6ac86ddd19c714021099df995733fcb1bd2e43fd0a1df4ec1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121449072"
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
