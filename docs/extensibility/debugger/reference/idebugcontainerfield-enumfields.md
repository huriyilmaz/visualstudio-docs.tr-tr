---
title: IDebugContainerField::EnumFields | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733230"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Kapsayıcının alanları için bir sayısallaştırıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parametreler
`dwKindFilter`\
[içinde] Numaralandırılacak alanları seçen [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sabitlerinin birleşimi. Alan türleri, sınıf veya ilkel veya yerel, parametre veya "bu" işaretçisi gibi belirli bilgiler gibi depolama türlerini açıklayabilir.

`dwModifiersFilter`\
[içinde] Numaralandırılacak alanları seçen [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) sabitlerinin birleşimi. Alan değiştiriciler, genel veya özel veya sanal, statik veya son gibi depolama bilgileri gibi izinlere erişebilir.

`pszNameFilter`\
[içinde] Numaralandırılacak alanın adı. Tüm alanlar döndürülecekse, bu null bir değer olabilir.

`nameMatch`\
[içinde] [Aramanın](../../../extensibility/debugger/reference/name-match.md) büyük/küçük harf duyarlı olup olmadığını kontrol eden NAME_MATCH numaralandırma değeri.

`ppEnum`\
[çıkış] Alanlar listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Alan yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, alan yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `dwKindFilter`Örneğin, `dwModifiersFilter`"MyMethod" adlı tüm genel sanal yöntemleri seçmek için , ve `pszNameFilter` parametreler birleştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
