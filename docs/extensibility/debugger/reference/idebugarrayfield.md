---
description: Bu arabirim bir dizi sembolünü veya türünü açıklar.
title: IDebugArrayField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f8de1ca4c8de27ab72087db7add6a75f4f7b77a940c7478c45e4647f37d74177
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239158"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Bu arabirim bir dizi sembolünü veya türünü açıklar.

## <a name="syntax"></a>Syntax

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan aynı nesne üzerinde kullanır. Bu arabirim, dizi nesnelerini temsil eden bir uzmanlıktır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) bayrağını döndürürse [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden bu arabirimi almak için [QueryInterface](/cpp/atl/queryinterface) `FIELD_TYPE_ARRAY` kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimleri üzerinde yöntemlere ek olarak şunları da sunar:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Dizide öğelerin sayısını alır.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Dizideki öğenin türünü alır.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Dizinin derecesini alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
