---
description: Bu arabirim bir değişken türünü temsil eder.
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 51606bfa15e8d8f6fbf8ce42364958b4fc888008
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064428"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Bu arabirim bir değişken türünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, sembol sağlayıcıları tarafından çalışma zamanında belirlenecek herhangi bir tür için temel sınıf olarak uygulanır. Bu yalnızca yönetilen koda göredir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, daha özel arabirimlerin türetilen bir temel sınıfı temsil eder.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim, kaynağından devralınan yöntemler dışında hiçbir yöntem `IDebugField` teminz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
