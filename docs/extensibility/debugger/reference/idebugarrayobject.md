---
description: Bu arabirim bir dizi nesnesini temsil eder.
title: Ihata ayıklama Garrayobject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16162cee8a02bf02b192336425101ec4bb579106
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158533"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim bir dizi nesnesini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 İfade değerlendirici bu arabirimi bir diziyi temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Nesne bir diziyi temsil ediyorsa, [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi bu arabirimi [QueryInterface](/cpp/atl/queryinterface) kullanarak elde edebilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Arabirimindeki yöntemlere ek olarak `IDebugObject` , arabiriminde aşağıdaki yöntemler uygulanır `IDebugArrayObject` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Dizideki öğelerin sayısını alır.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Dizinin bir öğesini alır.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Dizinin tüm öğelerini alır.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Dizinin derecesini alır.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Dizinin boyutlarını alır.|

## <a name="remarks"></a>Açıklamalar
 Bir ifade değerlendirici, bir ayrıştırma ağacındaki dizileri göstermek için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
