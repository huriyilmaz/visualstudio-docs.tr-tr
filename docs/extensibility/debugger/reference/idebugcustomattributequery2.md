---
title: IDebugCustomAttributeQuery2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732482"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Bu alan için özel bir öznitelik varlığını belirler ve varsa, öznitelik bilgilerini döndürür.

## <a name="syntax"></a>Sözdizimi

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcısı, özel öznitelikleri desteklemek için [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) uygulayan aynı nesne üzerinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda **IDebugCustomAttributeQuery** arabiriminin yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Özel bir özniteliğin ada göre var olup olmadığını belirler.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Verilen özel öznitelik için öznitelik bilgilerini alır.|

 **IDebugCustomAttributeQuery** yöntemlerine ek `IDebugCustomAttributeQuery2` olarak, aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Bu alana bağlı tüm özel öznitelikler için bir sayısallaştırıcı alır.|

## <a name="remarks"></a>Açıklamalar
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) yöntemi, bu alan için tanımlanan tüm özel öznitelikleri için bir sayısal ataertör döndürebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
