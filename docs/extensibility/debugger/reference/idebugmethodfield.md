---
title: IDebugMethodField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727068"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Bu arabirim bir yöntem açıklar.

## <a name="syntax"></a>Sözdizimi

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcısı bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan nesne üzerinde uygular. Bu arabirim, bir yöntem sunan bir uzmanlık alanıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) dönerse `FIELD_TYPE_METHOD` [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden bu arabirimi elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın. Buna ek olarak, yöntemleri, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), ve `IDebugMethodField` [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), tüm arayüzü dönmek.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugField ve IDebugContainerField](../../../extensibility/debugger/reference/idebugfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular: [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Yöntemin parametreleri için bir sayısallaştırıcı oluşturur.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Yöntemi içeren nesnenin "bu" işaretçisini alır.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Yöntemin tüm yerel değişkenleri için bir sayısallaştırıcı oluşturur.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Yöntemin seçili yerel değişkenleri için bir sayısallaştırıcı oluşturur.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Belirli bir özel öznitelik tanımlı olup olmadığını belirler.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Yöntemin statik yerel değişkenleri için bir sayısallaştırıcı oluşturur.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Yöntemin genel kapsayıcısını alır.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Yöntemi çağırmak için gereken her bağımsız değişkenin türü için bir sayısallaştırıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar
 Bir yöntem parametrelerin yanı sıra yerel değişkenleri de içerebilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
