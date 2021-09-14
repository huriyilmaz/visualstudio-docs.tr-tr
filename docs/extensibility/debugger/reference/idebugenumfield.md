---
description: Bu arabirim bir numaralama türünü temsil eder.
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fb8cb02d178a9efcb9b3d03423b722a4950c6511
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634913"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Bu arabirim bir numaralama türünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcısı, bir numaralama temsil etmek için bu arabirimi kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden bu arabirimi almak için [QueryInterface](/cpp/atl/queryinterface) `FIELD_TYPE_ENUM` kullanın.

## <a name="methods-in-vtable-order"></a>VTable sırasına göre yöntemler
 ve arabirimleri üzerinde `IDebugField` `IDebugContainerField` yöntemlerine ek olarak, bu arabirim aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Bu numaralama türünün adını açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Verilen değerle ilişkili sabit değerinin adını döndürür.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Verilen sabit sabit adı ile ilişkili değeri döndürür|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Verilen sabit sabit adı ile ilişkili değeri döndürür ancak büyük/büyük harf yoksayarak.|

## <a name="remarks"></a>Açıklamalar
 Bağlama ile bir konuma bağlı olan temel alınan [simgedir.](../../../extensibility/debugger/reference/idebugbinder-bind.md)

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bağlamak](../../../extensibility/debugger/reference/idebugbinder-bind.md)
