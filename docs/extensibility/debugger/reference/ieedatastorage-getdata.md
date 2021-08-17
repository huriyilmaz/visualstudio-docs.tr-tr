---
description: Nesneden belirtilen bayt sayısını alan.
title: IEEDataStorage::GetData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df7e30e966352a36983053d80f84f0ed4bc35f5bab577594bbefbc84c8b93879
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415734"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Nesneden belirtilen bayt sayısını alan.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Parametreler
`dataSize`\
[in] Alınacak bayt sayısı (dizi `data` en az bu bayt sayısını tut olmalıdır).

`sizeGotten`\
[out] Gerçekte alınan bayt sayısını döndürür.

`data`\
[in, out] İstenen verilerle doldurulması gereken dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin önerilen kullanımı, tüm veri baytlarını yerel bir diziye almaktır çünkü alma işlemi baytlarını atlamayı atlamanın bir yolu yoktur. Bu durumda, parametre `dataSize` [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) yöntemi tarafından döndürülen değer olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
