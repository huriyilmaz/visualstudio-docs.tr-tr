---
description: Bu arabirim bir işaretçi türünü temsil eder.
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: eba0654d97d37633ca1b2afce45b83de1a96bc1b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133087"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Bu arabirim bir işaretçi türünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı, bir işaretçiyi temsil etmek için bu arabirimi kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden bu arabirimi almak için [QueryInterface](/cpp/atl/queryinterface) `FIELD_TYPE_POINTER` kullanın.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 ve arabirimleri üzerinde yöntemlerine `IDebugField` `IDebugContainerField` ek olarak, bu arabirim aşağıdaki yöntemi kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|İşaretçinin hedefini açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|

## <a name="remarks"></a>Açıklamalar
 C/C++ içinde, bir işaretçi dizileme ile birlikte kullanılıyorsa bir kapsayıcı olabilir. Örneğin verilen , `char *pString` `pString` için bir işaretçi türüne `char` sahip. `pString[3]` , kapsayıcının dördüncü öğesine başvurulan `char` işaretçi olan kapsayıcı türüne sahip.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
