---
title: Ihata ayıklama Garrayfield | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736293"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Bu arabirim bir dizi sembolünü veya türünü açıklar.

## <a name="syntax"></a>Syntax

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Sembol sağlayıcısı, bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan aynı nesne üzerinde uygular. Bu arabirim, dizi nesnelerini temsil eden bir özelleşmenin bir özelleştirmesi.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) bayrağını döndürürse, bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden elde etmek için [QueryInterface](/cpp/atl/queryinterface) kullanın `FIELD_TYPE_ARRAY` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdakileri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Dizideki öğelerin sayısını alır.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Dizideki öğe türünü alır.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Dizinin derecesini alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
