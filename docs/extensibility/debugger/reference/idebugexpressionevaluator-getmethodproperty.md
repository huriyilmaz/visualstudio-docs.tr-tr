---
description: Bu yöntem yerelleri, bağımsız değişkenleri ve bir yöntemin diğer özelliklerini içeren bir özellik nesnesi alır.
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a2211477015ea1613549795caa597294d2f0ec779588afae7b97f462a929e0f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307524"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Bu yöntem yerelleri, bağımsız değişkenleri ve bir yöntemin diğer özelliklerini içeren bir özellik nesnesi alır.

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
[in] Kullanılacak sembol sağlayıcısı, [IDebugSymbolProvider nesnesi olarak ifade](../../../extensibility/debugger/reference/idebugsymbolprovider.md) edildi.

`pAddress`\
[in] Kodda [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi olarak ifadelenen ve en yakın içeren işleve çözümlenen adres.

`pBinder`\
[in] Kullanılacak bağlayıcı, [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi olarak ifade edildi.

`fIncludeHiddenLocals`\
[in] Sıfır olmayan ( `TRUE` ), gizli yerelleri dahil etmek anlamına gelir; sıfır ( `FALSE` ) gizli yerelleri dışarıda bırakmak anlamına gelir

`ppProperty`\
[out] yöntemini temsil [eden bir IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Gizli yerel ayarlar genellikle derleyici tarafından oluşturulan değişkenlerdir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
