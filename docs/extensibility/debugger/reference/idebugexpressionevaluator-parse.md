---
description: Bu yöntem, bir ifade dizesini ayrıştırıldı ifadeye dönüştürür.
title: IDebugExpressionEvaluator::P arse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac8b2c7a74801925775642bca9738865c207d14d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138750"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Bu yöntem, bir ifade dizesini ayrıştırıldı ifadeye dönüştürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parametreler
`upstrExpression`\
[in] Ayrıştırıla ifade dizesi.

`dwFlags`\
[in] İfadenin nasıl ayrıştır olacağını belirleyen [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) sabitleri koleksiyonu.

`nRadix`\
[in] Tüm sayısal bilgileri yorumlamak için kullanılacak radix.

`pbstrError`\
[out] Hatayı insan tarafından okunabilir metin olarak döndürür.

`pichError`\
[out] İfade dizesinde hatanın başlangıcının karakter konumunu döndürür.

`ppParsedExpression`\
[out] [IDebugParsedExpression nesnesinde ayrıştırılmış ifadeyi](../../../extensibility/debugger/reference/idebugparsedexpression.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem gerçek bir değer değil ayrıştıran bir ifade üretir. Ayrıştırıldı ifadesi değerlendirilmeye, yani bir değere dönüştürül etmeye hazırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
