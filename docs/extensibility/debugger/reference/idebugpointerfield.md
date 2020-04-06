---
title: IDebugPointerField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725598"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Bu arabirim bir işaretçi türünü temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcı, bir işaretçiyi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) dönerse `FIELD_TYPE_POINTER` [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden bu arabirimi elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim, `IDebugField` arabirimlerdeki `IDebugContainerField` yöntemlere ek olarak aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|İşaretçinin hedefini açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|

## <a name="remarks"></a>Açıklamalar
 C/C++'da, dizi gösterimi ile kullanılırsa işaretçi kapsayıcı olabilir. Örneğin, verilen `char *pString` `pString` , işaretçi türü `char`vardır. `pString[3]`bu kapsayıcının dördüncü öğesine `char` başvuran bir işaretçi olan bir kapsayıcı türüvardır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
