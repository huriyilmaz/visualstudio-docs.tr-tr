---
title: IDebugArrayField | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736293"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Bu arabirim sembolü veya türü açıklar.

## <a name="syntax"></a>Sözdizimi

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcı bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan nesne üzerinde uygular. Bu arabirim, dizi nesnelerini temsil eden bir uzmanlık alanıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) bayrağı `FIELD_TYPE_ARRAY`döndürürse, Bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugField ve IDebugContainerField](../../../extensibility/debugger/reference/idebugfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdakileri uygular: [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

|Yöntem|Açıklama|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Dizideki öğelerin sayısını alır.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Dizideki öğe türünü alır.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Dizinin sıralamasını alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
