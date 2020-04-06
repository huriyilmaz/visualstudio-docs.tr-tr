---
title: IEEDataStorage::Veri Get | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718217"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Nesneden belirtilen bayt sayısını alır.

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
[içinde] Alınacak bayt sayısı `data` (dizi en az bu sayıda bayt tutmalıdır).

`sizeGotten`\
[çıkış] Alınan bayt sayısını verir.

`data`\
[içinde, dışarı] İstenen verilerle doldurulacak dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Alma işleminde bayt atlamak için bir yol olmadığından, bu yöntemin önerilen kullanımı, yerel bir dizi içine tüm veri bayt almaktır. Bu durumda, parametre `dataSize` [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) yöntemi tarafından döndürülen değer olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
