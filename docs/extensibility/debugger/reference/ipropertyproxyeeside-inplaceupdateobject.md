---
description: Nesnenin verilerini verilen veri nesnesiyle güncelleştirir ve nesnenin yeni verilerini temsil eden yeni bir veri nesnesi döndürür.
title: 'IPropertyProxyEESide:: InPlaceUpdateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fb6c098d26148db39493b25f199c6819fb81d27
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082419"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Nesnenin verilerini verilen veri nesnesiyle güncelleştirir ve nesnenin yeni verilerini temsil eden yeni bir veri nesnesi döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametreler
`dataIn`\
'ndaki Yeni verileri içeren bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi.

`dataOut`\
dışı `IEEDataStorage` Değiştirilmiş verileri içeren yeni bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem gerçekte nesnenin verilerini günceller. Döndürülen [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesindeki verilerin gelen nesnedeki verilerle aynı olması gerekmez `IEEDataStorage` , ancak döndürülen nesne özelliğin geçerli değerini yansıtmalıdır.

 Gelen veri nesnesi genellikle EE tarafından uygulanmaz. Ancak, bu yöntemin döndürdüğü nesne her zaman EE tarafından uygulanır. Bu, her zaman her `IEEDataStorage` türlü sınıfa arayüzün uygulanmasını sağlar.

 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) yöntemi, gelen veri nesnesini temel alan bir veri nesnesi oluşturur, ancak özelliğin özgün verilerini etkilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
