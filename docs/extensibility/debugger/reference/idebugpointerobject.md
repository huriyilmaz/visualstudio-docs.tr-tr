---
title: Ihata ayıklama Gpoınterobject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 134c1edabb7df7a5cb7f26ce1b7b7487daa78e37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890207"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bu arabirim bir işaretçi nesnesini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 İfade değerlendirici bu arabirimi bir işaretçi nesnesini temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi, bir işaretçiyi temsil ediyorsa, bu arabirimi [QueryInterface](/cpp/atl/queryinterface) kullanarak elde edebilir `IDebugObject` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugObject nesnesinden](../../../extensibility/debugger/reference/idebugobject.md)devralınan yöntemlere ek olarak, `IDebugPointerObject` arabirim aşağıdaki yöntemleri sunar.

|Yöntem|Açıklama|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Arabirimin işaret ettiği nesneyi alır.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Arabirimin ardışık bayt dizisi olarak işaret ettiği değeri alır.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Arabirimin ardışık bayt dizisinden işaret ettiği değeri ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Bir ifade değerlendirici, bir ayrıştırma ağacındaki bir işaretçiyi temsil etmek için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
