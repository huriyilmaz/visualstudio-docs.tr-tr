---
title: 'Idebugexpressiondeğerlendirici:: GetMethodProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29a8e22301cbcd074c12d100d13601b57871a91a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930414"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Bu yöntem, bir yöntemin Yereller, bağımsız değişkenleri ve diğer özelliklerini içeren bir özellik nesnesi alır.

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
'ndaki Kullanılacak sembol sağlayıcısı bir [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi olarak ifade edilir.

`pAddress`\
'ndaki Koddaki, en yakın içeren işleve çözülmesi gereken bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi olarak ifade edilen adres.

`pBinder`\
'ndaki [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi olarak ifade edilen kullanılacak bağlayıcı.

`fIncludeHiddenLocals`\
'ndaki Sıfır dışında ( `TRUE` ) gizli Yereller dahil edilecek anlamına gelir; sıfır ( `FALSE` ) gizli Yereller dışında tutulacak anlamına gelir

`ppProperty`\
dışı Yöntemi temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Gizli Yereller genellikle derleyici tarafından oluşturulan değişkenlerdir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
