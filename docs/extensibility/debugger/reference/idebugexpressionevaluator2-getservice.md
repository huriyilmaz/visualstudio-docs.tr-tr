---
description: Benzersiz tanımlayıcısı verilen bir hizmet nesnesini alın.
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78719dbd33ea20e03fefd44f00cba3dd8b7f28e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088984"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Benzersiz tanımlayıcısı verilen bir hizmet nesnesini alın.

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
[in] Alınan hizmetin benzersiz tanımlayıcısı.

`ppService`\
[out] Hizmeti temsil eden bir nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu, başka bir ifade değerlendiriciden hizmet almak için bir üçüncü taraf ifade değerlendiricisi tarafından tüketilebilir. Örneğin, bu yöntem görselleştirici hizmetinin arabirimini varsayılan ifade değerlendiriciden almak için kullanılabilir. Üçüncü taraf ifade değerlendiricilerin bu arabirimi uygulaması pek olası değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
