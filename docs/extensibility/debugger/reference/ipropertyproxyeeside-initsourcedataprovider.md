---
description: Bu nesnenin kaynak verilerini başlatır ve ilk verileri içeren bir nesne döndürür.
title: 'IPropertyProxyEESide:: ınitsourcedataprovider | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18af1ffbce8d2e1dc38ecbff82bcf87e5a07160d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103162"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Bu nesnenin kaynak verilerini başlatır ve ilk verileri içeren bir nesne döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametreler
`dataOut`\
dışı Bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi döndürür

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, nesne verilerinde bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) arabirimi döndürebilmesi için bir nesneyi başlatmak için gereken her şeyi yapar. Bu, nesnenin verilerinin görüntülenmesine ve izin veriliyorsa bir tür görselleştiricisi tarafından değiştirilbilmesine izin verir.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
