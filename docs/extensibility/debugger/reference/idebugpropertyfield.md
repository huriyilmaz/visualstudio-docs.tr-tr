---
title: IDebugPropertyField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720689"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Bu arabirim, bir özelliğin alınıp ayarlanmasına izin veren işlevleri sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcısı bu arabirimi [IDebugContainerField'ı](../../../extensibility/debugger/reference/idebugcontainerfield.md)uygulayan aynı nesneye uygular. Bu arabirim, bir sınıftaki özellikler kavramını destekleyen bir uzmanlık alanıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemi dönerse, `FIELD_KIND_PROP`Bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 [IDebugField ve IDebugContainerField](../../../extensibility/debugger/reference/idebugfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular: [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Özelliği alan yöntemi alır.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Özelliği ayarlayan yöntemi alır.|

## <a name="remarks"></a>Açıklamalar
 Özellik yönetilen bir kod kavramıdır ve değişken olarak kabul edilen bir yöntemi temsil eder. Yönetilmeyen C++'da özellikler yok.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
