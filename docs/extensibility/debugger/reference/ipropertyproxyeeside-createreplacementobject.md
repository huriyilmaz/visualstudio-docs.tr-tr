---
description: İfade değerlendiricisine özgü bir veri nesnesinin kopyasını oluşturur (EE).
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d147e07fb87b016582373c46dd672f57daf1369
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029248"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
İfade değerlendiricisine özgü bir veri nesnesinin kopyasını oluşturur (EE).

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametreler
`dataIn`\
[in] Kopyalanan [verileri tutan bir IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi.

`dataOut`\
[out] Yeni bir nesne `IEEDataStorage` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yönteme, bir bayt [dizisini temsil eden bir IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi verilir. Bu gelen veri nesnesi genellikle veri kaynağı tarafından EE. Ancak, bu yöntem tarafından döndürülen nesne her zaman EE tarafından uygulanır ve bu da EE istenen sınıfa arabirimi `IEEDataStorage` uygulamasına olanak sağlar.

 Gelen nesne tarafından sağlanan verilerin `IEEDataStorage` giden nesnede aynı veriler olması gerektiğini `IEEDataStorage` unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
