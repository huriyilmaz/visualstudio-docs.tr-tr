---
description: Dizideki öğelerin sayısını alır.
title: 'Ihata ayıklama Garrayobject:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b70893b9fdcd3e957b8aa8bc2685e0845b49676da285c5661f477cae633311d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239171"
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
dışı Sayıyı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, dizi nesnesi çok boyutlu olsa bile, dizi nesnesinin tüm öğelerini tek boyutlu bir dizi olarak görür. Örneğin, dizi verildiğinde `myarray[3][2][6]` , bu yöntem parametresinde 36 döndürür `pdwElements` . Tek tek öğeleri tek tek almak için [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodunu kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
