---
description: Bu arabirim bir işaretçi türünü temsil eder.
title: Ihata ayıklama Gpoınterfield | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 86b2b1902532a3ab827d8e8d65ebc285973ff0bd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169723"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Bu arabirim bir işaretçi türünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Sembol sağlayıcısı bu arabirimi bir işaretçiyi temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden elde etmek için [QueryInterface](/cpp/atl/queryinterface) kullanın `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 `IDebugField`Ve arayüzlerindeki yöntemlere ek olarak `IDebugContainerField` , bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|İşaretçinin hedefini açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|

## <a name="remarks"></a>Açıklamalar
 C/C++ ' da, bir işaretçi dizi gösterimi ile kullanılıyorsa bir kapsayıcı olabilir. Örneğin, verilen `char *pString` , `pString` için bir işaretçi türüne sahiptir `char` . `pString[3]` , `char` o kapsayıcının dördüncü öğesine başvuran bir işaretçi olan bir kapsayıcı türüne sahiptir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
