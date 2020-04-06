---
title: IDebugProperty2::EnumChildren | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721517"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Tesisin çocuklarının listesini alır.

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
[içinde] [Numaralandırılmış](../../../extensibility/debugger/reference/debugprop-info-flags.md) [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılardaki hangi alanların dolduruleceğini belirten DEBUGPROP_INFO_FLAGS numaralandırmadaki bayrakların birleşimi.

`dwRadix`\
[içinde] Herhangi bir sayısal bilgi biçimlendirmede kullanılacak radix belirtir.

`guidFilter`\
[içinde] Hangi çocukların numaralandırılacak seçeceğini `dwAttribFilter` `pszNameFilter` `DEBUG_PROPERTY_INFO` seçmek için kullanılan filtrenin GUID ve parametreleri. Örneğin, `guidFilterLocals` yerel değişkenler için filtreler.

`dwAttribFilter`\
[içinde] [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) numaralandırmadan gelen ve örneğin `DBG_ATTRIB_METHOD` bu özelliğin çocukları olabilecek tüm yöntemler için numaralandırmak için ne tür nesneler olduğunu belirten bayrakların birleşimi. Parametreler `guidFilter` ve `pszNameFilter` parametrelerile birlikte kullanılır.

`pszNameFilter`\
[içinde] Hangi `guidFilter` `DEBUG_PROPERTY_INFO` çocukların numaralandırılmasını seçmek için kullanılan filtrenin adı ve `dwAttribFilter` parametreleri. Örneğin, bu parametreyi "MyX" adı olan tüm çocuklar için "MyX" filtrelerine ayarlamak.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden en büyük süreyi belirtir. Süresiz beklemek için kullanın. `INFINITE`

`ppEnum`\
[çıkış] Alt özelliklerin listesini içeren bir [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
