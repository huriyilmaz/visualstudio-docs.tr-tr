---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f14f24836beb1d69a15149a56a2817ebf14eff55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714905"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Bu nesnenin kaynak verilerini başolarak karşılar ve ilk verileri içeren bir nesneyi döndürür.

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
[çıkış] Bir [IEEDataStorage nesnesi](../../../extensibility/debugger/reference/ieedatastorage.md) döndürür

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, nesnenin verilerinde bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) arabirimi döndürebilmek için bir nesneyi başlatmaiçin ne gerekiyorsa yapar. Bu, nesnenin verilerinin görüntülenmesini ve izin verildiği takdirde bir tür görselleştiricisi tarafından değiştirilmesini sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
