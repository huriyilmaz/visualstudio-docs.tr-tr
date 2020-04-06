---
title: IDebugDynamicField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731317"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Bu arabirim bir değişken türünü temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, çalışma zamanında belirlenebilen herhangi bir tür için taban sınıf olarak sembol sağlayıcılar tarafından uygulanır. Bu yalnızca yönetilen kod içindir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, daha özel arabirimlerin türetilebileceği bir taban sınıfı temsil eder.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim, devralınanlar dışında herhangi `IDebugField`bir yöntem sağlamaz.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
