---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 303ff1820d0213766ec5ad186ce7b9a3483c0bfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909855"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Bu arabirim bir özelliği almaya ve ayarlamaya izin veren işlevleri sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)uygulayan aynı nesne üzerinde uygular. Bu arabirim, bir sınıftaki özellik kavramını destekleyen bir özelleşmenin bir özelleştirmesi.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemi döndürürse, bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden elde etmek için [QueryInterface](/cpp/atl/queryinterface) kullanın `FIELD_KIND_PROP` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Özelliği alan yöntemi alır.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Özelliği ayarlayan yöntemi alır.|

## <a name="remarks"></a>Açıklamalar
 Özelliği, yönetilen bir kod kavramıdır ve değişken olarak ele alan bir yöntemi temsil eder. Yönetilmeyen C++ içinde özellikler yok.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
