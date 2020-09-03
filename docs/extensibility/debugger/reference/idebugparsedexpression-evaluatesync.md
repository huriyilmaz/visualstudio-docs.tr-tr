---
title: 'IDebugParsedExpression:: EvaluateSync | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726012"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Bu yöntem ayrıştırılmış ifadeyi değerlendirir ve isteğe bağlı olarak sonucu başka bir veri türüne yayınlar.

## <a name="syntax"></a>Söz dizimi

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
'ndaki İfadenin nasıl değerlendirileceğini denetleyen [Evalflags](../../../extensibility/debugger/reference/evalflags.md) sabitlerinin bir birleşimi.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. `INFINITE`Sonsuza kadar beklemek için kullanın.

`pSymbolProvider`\
'ndaki Bir [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimi olarak ifade edilen sembol sağlayıcısı.

`pAddress`\
'ndaki Bir yöntem içinde bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimi olarak ifade edilen geçerli yürütme konumu.

`pBinder`\
'ndaki [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi olarak ifade edilen cilt.

`bstrResultType`\
'ndaki Sonucun türüne dönüştürülmesi gereken tür. Bu bağımsız değişken null bir değer olabilir.

`ppResult`\
dışı Değerlendirmenin sonuçlarını temsil eden [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İfade değerlendirme bağlamı tarafından verilir; Bu, `pAddress` kapsayan yöntemi belirlemeyi ve sonra, ifadedeki simgelerin değerini belirlemek için dil kapsamı kurallarını kullanmayı mümkün kılar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
