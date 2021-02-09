---
title: 'Idebugexpressiondeğerlendirici:: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13759bc8598c4739fbb9d2263dd8dc7d1b84c16e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930427"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Bu yöntem, bir yöntem konumunu ve sapmayı bir bellek adresine dönüştürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parametreler
`upstrFullyQualifiedMethodPlusOffset`\
'ndaki Yöntem konumu ve değeri dize olarak ifade edilir.

`pSymbolProvider`\
'ndaki Bir [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi olarak ifade edilen sembol sağlayıcısı.

`pAddress`\
'ndaki Yöntemi içindeki bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi olarak ifade edilen adres.

`pBinder`\
'ndaki [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi olarak ifade edilen bağlayıcı.

`ppProperty`\
dışı Bellek adresini temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen adres, örneğin bir kesme noktası ayarlamak için kullanılabilir.

 Ada rağmen `upstrFullyQualifiedMethodPlusOffset` Bu parametreye kısmen nitelenmiş bir yöntem adı geçirilebilir. Bu durumda, seçilen yöntem içine eklenen bir yöntemdir `pAddress` . Bu parametrenin yorumlanması, ifade değerlendiricisi 'nin ve desteklediği dilin uygulamasına göre yapılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
