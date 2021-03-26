---
description: Benzersiz tanımlayıcısı verilen bir hizmet nesnesini alır.
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9c595d2a3a4551920e17a9ad8d8a13b5ae4ab0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092013"
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
'ndaki Alınacak hizmetin benzersiz tanıtıcısı.

`ppService`\
dışı Hizmeti temsil eden bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, başka bir ifade değerlendiricisinde hizmet elde etmek için üçüncü taraf bir ifade değerlendirici tarafından tüketilebilir. Örneğin, bu yöntem varsayılan ifade değerlendiricisi ' nden Görselleştirici hizmeti arabirimini almak için kullanılabilir. Üçüncü taraf ifadesi değerlendiricileri bu arabirimin uygulanması için gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
