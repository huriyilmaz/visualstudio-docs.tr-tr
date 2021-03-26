---
description: Bu nesnede bulunan bayt sayısını döndürür.
title: 'IEEDataStorage:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 632d2adeaca976d0bb3fdfbe1b88571e337e02dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083537"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Bu nesnede bulunan bayt sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parametreler
`size`\
dışı Bu nesnede bulunan baytların sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Asıl veri baytlarını almak için [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [Veri Al](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
