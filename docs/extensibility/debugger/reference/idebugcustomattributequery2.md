---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732482"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Bu alan için özel bir özniteliğin varlığını belirler ve varsa, öznitelik bilgilerini döndürür.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, özel öznitelikleri desteklemek için [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 'ı uygulayan aynı nesne üzerinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden almak için [QueryInterface](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, **ıdebugcustomattributequery** arabiriminin yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Özel bir özniteliğin ada göre varolup olmadığını belirler.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Verilen özel öznitelik için öznitelik bilgilerini alır.|

 **Idebugcustomattributequery** yöntemlerine ek olarak, `IDebugCustomAttributeQuery2` aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Bu alana eklenen tüm özel öznitelikler için bir Numaralandırıcı alır.|

## <a name="remarks"></a>Açıklamalar
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) yöntemi, bu alan için tanımlanan tüm özel öznitelikler için bir Numaralandırıcı döndürebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
