---
description: Nesneden belirtilen bayt sayısını alır.
title: 'IEEDataStorage:: GetData | Microsoft Docs'
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
ms.openlocfilehash: 0d8f646e137d5709bb49acac9074a1ad08981ffa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137892"
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
'ndaki Alınacak bayt sayısı ( `data` dizi en az bu sayıda bayt olmalıdır).

`sizeGotten`\
dışı Gerçekten alınan bayt sayısını döndürür.

`data`\
[in, out] İstenen verilerle doldurulacak dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin önerilen kullanımı, alma işlemindeki baytları atlamak için bir yol olmadığından, tüm veri baytlarını yerel bir diziye almak olacaktır. Bu durumda, parametresi `dataSize` [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) yönteminin döndürdüğü değer olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
