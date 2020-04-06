---
title: IDebugStackFrame2::EnumProperties | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f822f20cf4fb7a6fd5aa71b9cc1ec26bcd90e234
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719905"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Yerel değişkenler gibi yığın çerçevesiyle ilişkili özellikler için bir sayısallaştırıcı oluşturur.

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
[içinde] [Numaralandırılmış](../../../extensibility/debugger/reference/debugprop-info-flags.md) [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılardaki hangi alanların dolduruleceğini belirten DEBUGPROP_INFO_FLAGS numaralandırmadaki bayrakların birleşimi.

`nRadix`\
[içinde] Herhangi bir sayısal bilgi biçimlendirmede kullanılacak radix.

`refiid`\
[içinde] Hangi [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapıların numaralandırılmak üzere kullanılacağını seçmek için `guidFilterLocals`kullanılan bir filtrenin GUID'i.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden maksimum süre. Süresiz beklemek için kullanın. `INFINITE`

`pcelt`\
[çıkış] Numaralandırılmış özellik sayısını verir. Bu, [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) yöntemini aramakla aynıdır.

`ppEnum`\
[çıkış] İstenilen özelliklerin listesini içeren bir [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, seçili tüm özelliklerin tek bir çağrıyla alınmasını sağladığından, [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) ve [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemlerini sırayla aramaktan daha hızlıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
