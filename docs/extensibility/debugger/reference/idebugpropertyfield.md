---
description: Bu arabirim, özellik alma ve ayarlamaya olanak sağlayan işlevleri sağlar.
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d4e0780f43953bdf7afb10e2d038ce46b794d3dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071103"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Bu arabirim, özellik alma ve ayarlamaya olanak sağlayan işlevleri sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı bu arabirimi [IDebugContainerField'i uygulayan aynı nesnede kullanır.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Bu arabirim, bir sınıftaki özellikler kavramını destekleyen bir uzmanlıktır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemi döndürse [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden almak için [QueryInterface](/cpp/atl/queryinterface) `FIELD_KIND_PROP` kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimleri üzerinde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|özelliğini alan yöntemini alır.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|özelliğini ayaran yöntemi alır.|

## <a name="remarks"></a>Açıklamalar
 Özellik, yönetilen kod kavramıdır ve değişken olarak kabul edilen bir yöntemi temsil eder. Özellikler, unmanaged C++ içinde mevcut değildir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
