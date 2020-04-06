---
title: IDebugEnumField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7885f36a113809e81279498a769e257af4f1cde2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730177"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Bu arabirim bir numaralandırma türünü temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcı, numaralandırmayı temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) dönerse `FIELD_TYPE_ENUM` [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden bu arabirimi elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>VTable sırasına göre yöntemler
 Bu arabirim, `IDebugField` arabirimlerdeki `IDebugContainerField` yöntemlere ek olarak aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Bu numaralandırma türü için adı açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Verilen değerle ilişkili numaralandırma sabitinin adını verir.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Verilen numaralandırma sabit adı ile ilişkili değeri verir|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Verilen numaralandırma sabit adı ile ilişkili değeri döndürür, ancak durum yoksayma.|

## <a name="remarks"></a>Açıklamalar
 Aslında [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)ile bir konuma bağlı altta yatan semboldür.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bağla](../../../extensibility/debugger/reference/idebugbinder-bind.md)
