---
title: IDebugMethodField::EnumAllLocals | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727338"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Bir derleyici tarafından dahili olarak oluşturulanlar da dahil olmak üzere yöntemin tüm yerel değişkenleri için bir sayısallaştırıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
[içinde] Yöntem içinde hata ayıklama adresini temsil eden ve belirli bir kapsam veya içeriğe işaret eden bir [Hata](../../../extensibility/debugger/reference/idebugaddress.md) Adresi nesnesi.

`ppLocals`\
[çıkış] Belirtilen kapsamdaki tüm yerel halkların listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür; aksi takdirde, hiçbir yerel gösteren null bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, yerel halk yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Yalnızca verilen hata ayıklama adresini içeren blok içinde tanımlanan değişkenler numaralandırılır. Bu yöntem derleyici tarafından oluşturulan yerel içerir. Tüm bu gerekli olan açıkça kaynak ta tanımlanan yerliler ise, [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) yöntemini arayın.

 Yöntem, birden çok kapsam bağlamı veya blok içerebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
