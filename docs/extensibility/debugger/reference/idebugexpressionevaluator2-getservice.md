---
title: IDebugExpressionEvaluator2::GetService | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729353"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Benzersiz tanımlayıcısı verilen bir hizmet nesnesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Parametreler
`uid`\
[içinde] Alınacak hizmetin benzersiz tanımlayıcısı.

`ppService`\
[çıkış] Hizmeti temsil eden bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, başka bir ifade değerlendiricisinden hizmet almak için üçüncü taraf ifade değerlendiricisi tarafından tüketilebilir. Örneğin, bu yöntem varsayılan ifade değerlendiricisi nden visualizer hizmeti için arabirim elde etmek için kullanılabilir. Üçüncü taraf ifade değerlendiriciler bu arabirimi uygulamak için gereken olası değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
