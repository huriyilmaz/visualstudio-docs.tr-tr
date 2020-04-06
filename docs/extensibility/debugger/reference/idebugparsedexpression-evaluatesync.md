---
title: IDebugParsedExpression::Sync | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726012"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Bu yöntem ayrışmış ifadeyi değerlendirir ve isteğe bağlı olarak sonucu başka bir veri türüne atar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parametreler
`dwEvalFlags`\
[içinde] İfadenin nasıl değerlendirileceğini kontrol eden [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) sabitlerinin birleşimi.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden en büyük süreyi belirtir. Süresiz beklemek için kullanın. `INFINITE`

`pSymbolProvider`\
[içinde] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimi olarak ifade edilen sembol sağlayıcısı.

`pAddress`\
[içinde] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimi olarak ifade edilen bir yöntem içindeki geçerli yürütme konumu.

`pBinder`\
[içinde] Bağlayıcı, bir [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi olarak ifade edilir.

`bstrResultType`\
[içinde] Sonucun döküm olması gereken tür. Bu bağımsız değişken null bir değer olabilir.

`ppResult`\
[çıkış] Değerlendirme sonuçlarını temsil eden [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İfade değerlendirme `pAddress`bağlamı, içeren yöntemi belirlemeyi ve ifadedeki sembollerin değerini belirlemek için dil kapsam kurallarını kullanmayı mümkün kılan tarafından verilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
