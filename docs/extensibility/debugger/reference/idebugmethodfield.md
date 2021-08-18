---
description: Bu arabirim bir yöntemi açıklar.
title: IDebugMethodField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2c06cf4315bdd1595985ad7170fb7b46f1f33316
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126966"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Bu arabirim bir yöntemi açıklar.

## <a name="syntax"></a>Syntax

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan aynı nesnede kullanır. Bu arabirim, bir yöntem sunan bir uzmanlıktır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden almak için [QueryInterface](/cpp/atl/queryinterface) `FIELD_TYPE_METHOD` kullanın. Ayrıca, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)ve [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)yöntemleri `IDebugMethodField` arabirimini geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimleri üzerinde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|yönteminin parametreleri için bir numaralayıcı oluşturur.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|yöntemini içeren nesnenin "bu" işaretçisini alır.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|yönteminin tüm yerel değişkenleri için bir numaralayıcı oluşturur.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|yönteminin seçili yerel değişkenleri için bir numaralayıcı oluşturur.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Belirli bir özel özniteliğin tanımlanmamış olup olmadığını belirler.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|yönteminin statik yerel değişkenleri için bir numaralayıcı oluşturur.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|yönteminin genel kapsayıcıyı alır.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|yöntemini çağıran her bağımsız değişkenin türü için bir numaralayıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar
 Bir yöntem hem parametreleri hem de yerel değişkenleri içerebilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
