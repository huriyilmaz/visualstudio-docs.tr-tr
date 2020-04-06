---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729526"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Bu yöntem, yöntem konumunu dönüştürür ve bellek adresine ofset.

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
[içinde] Yöntem konumu ve ofset, bir dize olarak ifade.

`pSymbolProvider`\
[içinde] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi olarak ifade edilen sembol sağlayıcı.

`pAddress`\
[içinde] Yöntem içinde bir adres, bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi olarak ifade.

`pBinder`\
[içinde] Bağlayıcı bir [IDebugBinder nesnesi](../../../extensibility/debugger/reference/idebugbinder.md) olarak ifade edilir.

`ppProperty`\
[çıkış] Bellek adresini temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen adres, örneğin bir kesme noktası ayarlamak için kullanılabilir.

 Adı `upstrFullyQualifiedMethodPlusOffset`rağmen , Bu parametre kısmen nitelikli yöntem adı geçirilebilir. Bu durumda, seçili yöntem içine alan `pAddress`biridir. Bu parametrenin nasıl yorumlanacağı ifade değerlendiricinin uygulanmasına ve desteklediği dile kadardır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
