---
title: IPropertyProxyEESide::InplaceUpdateObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714901"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Nesnenin verilerini verilen veri nesnesiyle güncelleştirir ve nesnenin yeni verilerini temsil eden yeni bir veri nesnesini döndürür.

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
[içinde] Yeni verileri içeren bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi.

`dataOut`\
[çıkış] Değiştirilen verileri `IEEDataStorage` içeren yeni bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem aslında nesnenin verilerini güncelleştirir. Döndürülen [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesindeki verilerin gelen `IEEDataStorage` nesnedeki verilerle aynı olması gerekmez, ancak döndürülen nesnenin özelliğin geçerli değerini yansıtması gerekir.

 Gelen veri nesnesi genellikle EE tarafından uygulanmaz. Ancak, bu yöntemle döndürülen nesne her zaman EE tarafından uygulanır `IEEDataStorage` ve bu da EE'nin arabirimi istenilen sınıfa uygulamasına olanak tanır.

 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) yöntemi, gelen veri nesnesini temel alan bir veri nesnesi oluşturur, ancak özelliğin özgün verilerini etkilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
