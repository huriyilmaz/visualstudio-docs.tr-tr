---
description: Nesnenin verilerini verilen veri nesnesiyle günceller ve nesnenin yeni verilerini temsil eden yeni bir veri nesnesi döndürür.
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 908b952be10f5789c1bdbdec007540e83393b8e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118131"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Nesnenin verilerini verilen veri nesnesiyle günceller ve nesnenin yeni verilerini temsil eden yeni bir veri nesnesi döndürür.

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
[in] Yeni [verileri içeren bir IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi.

`dataOut`\
[out] Değiştirilmiş verileri `IEEDataStorage` içeren yeni bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem aslında nesnenin verilerini günceller. Döndürülen [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesinde yer alan verilerin gelen nesnede yer alan veriyle aynı olması gerek yoktur, ancak döndürülen nesnenin özelliğin geçerli değerini `IEEDataStorage` yansıtması gerekir.

 Gelen veri nesnesi genellikle veri kaynağı tarafından EE. Ancak, bu yöntem tarafından döndürülen nesne her zaman EE tarafından uygulanır ve bu da EE istenen sınıfa arabirimi `IEEDataStorage` uygulamasına olanak sağlar.

 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) yöntemi, gelen veri nesnesini temel alan bir veri nesnesi oluşturur, ancak özelliğin özgün verilerini etkilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
