---
description: Bu arabirim bir sabit listesi türünü temsil eder.
title: Ihata ayıklama Genumfield | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 18671f8f719dc797709677a14417eaa0a54aaea2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092533"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Bu arabirim bir sabit listesi türünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, bir numaralandırmayı temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden elde etmek için [QueryInterface](/cpp/atl/queryinterface) kullanın `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>VTable sırasındaki Yöntemler
 `IDebugField`Ve arayüzlerindeki yöntemlere ek olarak `IDebugContainerField` , bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Bu numaralandırma türü için adı açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Verilen değerle ilişkili sabit listesi sabitinin adını döndürür.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Verilen sabit listesi sabit adıyla ilişkili değeri döndürür|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Verilen sabit listesi sabit adıyla ilişkili değeri döndürür, ancak büyük/küçük harf yok sayılıyor.|

## <a name="remarks"></a>Açıklamalar
 Aslında [bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)ile bir konuma bağlı olan temel simgedir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bağladığınızda](../../../extensibility/debugger/reference/idebugbinder-bind.md)
