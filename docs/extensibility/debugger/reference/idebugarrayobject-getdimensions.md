---
description: Dizinin boyutlarını alır.
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e637f1139de8ee6caebea92cc5ca1fe494c206e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080019"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Dizinin boyutlarını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parametreler
`dwCount`\
[in] Alınan boyut sayısı.

`dwDimensions`\
[in, out] Her boyutun boyutlarıyla doldurulmuş bir dizi. `dwCount` dizinin en büyük boyutunu `dwDimensions` belirtir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Çok boyutlu bir dizi, her boyut için farklı boyutlara sahip olabilir. Örneğin, üç boyutlu dizisine göre, bu yöntem bu sırayla parametresinde `myarray[3][2][6]` 3, 2 ve 6 `dwDimensions` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
