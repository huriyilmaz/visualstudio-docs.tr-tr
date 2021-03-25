---
description: İfade değerlendirici (EE) öğesine özel bir veri nesnesinin kopyasını oluşturur.
title: 'IPropertyProxyEESide:: CreateReplacementObject | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 460052ceb9f2f90a5123f4cc646682919f96dc94
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082588"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
İfade değerlendirici (EE) öğesine özel bir veri nesnesinin kopyasını oluşturur.

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
'ndaki Kopyalanacak verileri tutan bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi.

`dataOut`\
dışı Yeni bir `IEEDataStorage` nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yönteme, bir bayt dizisini temsil eden bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi verilir. Bu gelen veri nesnesi genellikle EE tarafından uygulanmaz. Ancak, bu yöntemin döndürdüğü nesne her zaman EE tarafından uygulanır. Bu, her zaman her `IEEDataStorage` türlü sınıfa arayüzün uygulanmasını sağlar.

 Gelen nesne tarafından sağlanan verilerin `IEEDataStorage` giden nesnedeki verilerle aynı olması gerektiğini unutmayın `IEEDataStorage` .

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
