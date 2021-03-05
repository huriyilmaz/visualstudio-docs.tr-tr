---
description: Bu yöntem, bu nesneyle ilişkili bağımsız değişken türlerinin bir listesini alır.
title: 'IDebugBinder3:: GetTypeArguments | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74cbd6e67a82113e43226ded8640630be50ba086
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173903"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Bu yöntem, bu nesneyle ilişkili bağımsız değişken türlerinin bir listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Parametreler
`skip`\
'ndaki Bağımsız değişken türlerini almadan önce atlanacak alan sayısı.

`count`\
'ndaki Döndürülecek bağımsız değişken alanı sayısı (Ayrıca dizinin boyutunu belirtir `ppFields` ).

`ppFields`\
[in, out] Bu yöntemin döndürülme sonunda doldurulacak alanlar dizisi.

`pFetched`\
[out] \( isteğe bağlı) aslında döndürülen bağımsız değişken türü alanlarının sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bağımsız değişken türlerinin sayısı, önceden [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)ile alınabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
