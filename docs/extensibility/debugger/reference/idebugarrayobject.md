---
title: IDebugArrayObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736218"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim bir dizi nesnesi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi bir diziyi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Nesne bir diziyi temsil ediyorsa, [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi [QueryInterface'i](/cpp/atl/queryinterface) kullanarak bu arabirimi elde edebilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 `IDebugObject` Arabirimdeki yöntemlere ek olarak, `IDebugArrayObject` arabirimde aşağıdaki yöntemler uygulanır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Dizideki öğelerin sayısını alır.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Dizinin bir öğesini alır.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Dizinin tüm öğelerini alır.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Dizinin sıralamasını alır.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Dizinin boyutlarını alır.|

## <a name="remarks"></a>Açıklamalar
 Bir ifade değerlendiricisi, ayrışma ağacındaki dizileri temsil etmek için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
