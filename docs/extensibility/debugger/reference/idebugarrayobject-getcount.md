---
title: IDebugArrayObject::GetCount | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736203"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Dizideki öğelerin sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parametreler
`pdwElements`\
[çıkış] Sayımı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, dizi nesnesi çok boyutlu olsa bile, bir dizi nesnesinin tüm öğelerini tek boyutlu bir dizi olarak görür. Örneğin, dizi `myarray[3][2][6]`göz önüne alındığında, bu yöntem `pdwElements` parametre 36 döndürecek. Tek tek öğeleri tektek almak için [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
