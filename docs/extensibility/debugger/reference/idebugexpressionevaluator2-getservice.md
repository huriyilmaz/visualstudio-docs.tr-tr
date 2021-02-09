---
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb0f822011a5f54cf97e58f53ec1cf03b5d26a23
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926344"
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
