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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729526"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Bu yöntem, bir yöntem konumunu ve sapmayı bir bellek adresine dönüştürür.

## <a name="syntax"></a>Söz dizimi

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
