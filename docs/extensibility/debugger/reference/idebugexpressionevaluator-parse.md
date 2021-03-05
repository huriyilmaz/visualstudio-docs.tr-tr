---
description: Bu yöntem, bir ifade dizesini ayrıştırılmış ifadeye dönüştürür.
title: Idebugexpressiondeğerlendirici::P arde | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6a586c7e7cac1a4ef034b7941840db59d376180
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152500"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Bu yöntem, bir ifade dizesini ayrıştırılmış ifadeye dönüştürür.

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
'ndaki Ayrıştırılacak ifade dizesi.

`dwFlags`\
'ndaki İfadenin nasıl ayrıştırılaceğini tespit eden bir [Parseflags](../../../extensibility/debugger/reference/parseflags.md) sabitleri koleksiyonu.

`nRadix`\
'ndaki Sayısal bilgileri yorumlamak için kullanılacak taban tabanı.

`pbstrError`\
dışı Hatayı insanlarca okunabilir metin olarak döndürür.

`pichError`\
dışı İfade dizesinde hatanın başlangıcı olan karakter konumunu döndürür.

`ppParsedExpression`\
dışı Bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesinde ayrıştırılmış ifadeyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, gerçek bir değer değil ayrıştırılmamış bir ifade oluşturur. Ayrıştırılmış bir ifade değerlendirilmeye, yani bir değere dönüştürülecek.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
