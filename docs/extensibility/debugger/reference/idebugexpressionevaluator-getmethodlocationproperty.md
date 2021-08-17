---
description: Bu yöntem yöntem konumunu ve uzaklığı bir bellek adresine dönüştürür.
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e5b520fc15d5cd1edff3331f4622c6086b3b58d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096186"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Bu yöntem yöntem konumunu ve uzaklığı bir bellek adresine dönüştürür.

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
[in] Yöntem konumu ve uzaklığı, dize olarak ifade edildi.

`pSymbolProvider`\
[in] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi olarak ifade eden sembol sağlayıcısı.

`pAddress`\
[in] Yöntemin içindeki bir adres, [IDebugAddress nesnesi olarak ifade](../../../extensibility/debugger/reference/idebugaddress.md) edildi.

`pBinder`\
[in] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi olarak ifade eden bağlayıcı.

`ppProperty`\
[out] Bellek adresini [temsil eden bir IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen adres, örneğin bir kesme noktası ayarlamak için kullanılabilir.

 adına `upstrFullyQualifiedMethodPlusOffset` rağmen, bu parametre kısmen nitelikli bir yöntem adı geçirebilirsiniz. Bu durumda, seçilen yöntem içine alan `pAddress` yöntemdir. Bu parametrenin nasıl yorumlanması, ifade değerlendiricinin uygulanmasına ve desteklediği dile göredir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
