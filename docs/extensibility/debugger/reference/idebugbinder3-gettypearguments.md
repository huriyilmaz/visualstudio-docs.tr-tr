---
title: IDebugBinder3::GetTypeArguments | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7667b06348c5e1b2865b24ab49095772808d6c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735695"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Bu yöntem, bu nesne ile ilişkili bağımsız değişken türlerinin listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Parametreler
`skip`\
[içinde] Bağımsız değişken türlerini almadan önce atlayacak alan sayısı.

`count`\
[içinde] Döndürülecek bağımsız değişken alanlarının sayısı `ppFields` (dizinin boyutunu da belirtir).

`ppFields`\
[içinde, dışarı] Bu yöntemin dönüşünde doldurulacak bir dizi alan.

`pFetched`\
[çıkış] \(isteğe bağlı) Bağımsız değişken türü alanların sayısı gerçekte döndürülür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bağımsız değişken türlerinin sayısı [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)ile önceden elde edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
