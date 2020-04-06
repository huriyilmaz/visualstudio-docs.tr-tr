---
title: ipropertyproxyeeside::createreplacementobject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715035"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
İfade değerlendiricisine (EE) özgü bir veri nesnesinin kopyasını oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametreler
`dataIn`\
[içinde] Kopyalanacak verileri tutan bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi.

`dataOut`\
[çıkış] Yeni `IEEDataStorage` bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bayt bir dizi temsil eden bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesneverilir. Bu gelen veri nesnesi genellikle EE tarafından uygulanmaz. Ancak, bu yöntemle döndürülen nesne her zaman EE tarafından uygulanır `IEEDataStorage` ve bu da EE'nin arabirimi istenilen sınıfa uygulamasına olanak tanır.

 Gelen `IEEDataStorage` nesne tarafından sağlanan verilerin giden `IEEDataStorage` nesnedeki aynı veriler olması gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
