---
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729511"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Bu yöntem, bir yöntemin yerel, bağımsız değişkenler ve diğer özelliklerini içeren bir özellik nesnesi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parametreler
`pSymbolProvider`\
[içinde] Kullanılacak sembol sağlayıcı, [iDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi olarak ifade edilir.

`pAddress`\
[içinde] Koddaki adres, [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi olarak ifade edilir ve en yakın içeren işleve çözülmelidir.

`pBinder`\
[içinde] Kullanılacak bağlayıcı, bir [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi olarak ifade edilir.

`fIncludeHiddenLocals`\
[içinde] Nonzero`TRUE`( )gizli yerlileri dahil etmek anlamına gelir; sıfır`FALSE`( ) gizli yerlileri dışarıda bırakmak anlamına gelir

`ppProperty`\
[çıkış] Yöntemi temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Gizli yerel değişkenler genellikle derleyici tarafından oluşturulan değişkenlerdir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
