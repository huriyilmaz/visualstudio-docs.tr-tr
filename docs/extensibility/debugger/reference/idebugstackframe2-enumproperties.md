---
description: Yerel değişkenler gibi yığın çerçevesiyle ilişkili özellikler için bir numaralayıcı oluşturur.
title: IDebugStackFrame2::EnumProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b917bc14728ee1f8dd37f28bbec42e395455ee35
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725136"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Yerel değişkenler gibi yığın çerçevesiyle ilişkili özellikler için bir numaralayıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`dwFieldSpec`\
[in] Numaralandırılan [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) alanları belirten bir numaralandırılan DEBUG_PROPERTY_INFO bayrakların birleşimi. [](../../../extensibility/debugger/reference/debug-property-info.md)

`nRadix`\
[in] Herhangi bir sayısal bilgiyi biçimlendirmek için kullanılacak radyan.

`refiid`\
[in] Hangi filtre yapılarının numaralandır [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) seçmek için kullanılan bir FILTRE GUID'si, örneğin: `guidFilterLocals` .

`dwTimeout`\
[in] Bu yöntemden dönmeden önce bek süresi (milisaniye cinsinden). Süresiz `INFINITE` olarak beklemek için kullanın.

`pcelt`\
[out] Numara verilen özelliklerin sayısını döndürür. Bu, GetCount yöntemini [çağırmayla aynıdır.](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)

`ppEnum`\
[out] İstenen özelliklerin [listesini içeren bir IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, seçilen tüm özelliklerin tek bir çağrıyla alınmasına izin verir, [sırayla GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) ve [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemlerini çağırmadan daha hızlıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
