---
description: Dizinin boyutlarını alır.
title: 'Ihata ayıklama Garrayobject:: GetDimensions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5bb935ea4aba6ab6ebd0a39f8dfc8d539d6555c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158689"
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
'ndaki Alınacak boyut sayısı.

`dwDimensions`\
[in, out] Her boyutun boyutlarıyla doldurulmuş bir dizi. `dwCount` dizinin en büyük boyutunu belirtir `dwDimensions` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Çok boyutlu bir dizi, her boyut için farklı boyutlarda olabilir. Örneğin, üç boyutlu dizi verildiğinde `myarray[3][2][6]` , bu yöntem bu sırada parametreye 3, 2 ve 6 döndürür `dwDimensions` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
