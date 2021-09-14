---
description: Kapsayıcının alanları için bir numaralayıcı oluşturur.
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 582521a59cc4652aaf3bdf92f5f0c24b19283e20
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725264"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Kapsayıcının alanları için bir numaralayıcı oluşturur.

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
[in] Numaralara [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) alanları seçen sabit sabitlerinin birleşimi. Alan türleri, sınıf veya ilkel gibi depolama türlerini ya da yerel, parametre veya "bu" işaretçi gibi belirli bilgileri açıklar.

`dwModifiersFilter`\
[in] Numaralara [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) alanları seçen sabit sabitlerinin birleşimi. Alan değiştiricileri genel veya özel gibi erişim izinleri veya sanal, statik veya son gibi depolama bilgileri olabilir.

`pszNameFilter`\
[in] Numaralandı olacak alanın adı. Tüm alanlar döndürülacaksa bu değer null değer olabilir.

`nameMatch`\
[in] Aramanın [büyük/NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) olup olmadığını kontrol eden bir değerdir.

`ppEnum`\
[out] Alan listesini [temsil eden bir IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Alan yoksa null değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK veya S_FALSE yoksa bu işlevi döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin `dwKindFilter` `dwModifiersFilter` , ve parametreleri `pszNameFilter` birleştirerek "MyMethod" adlı tüm genel sanal yöntemleri seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
