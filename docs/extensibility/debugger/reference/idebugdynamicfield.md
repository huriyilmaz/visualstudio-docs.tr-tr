---
description: Bu arabirim bir değişkenin türünü temsil eder.
title: Idebugdynamicfield | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: bf1d72bfa38e6af0419e696b267699d10340cc68
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094087"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Bu arabirim bir değişkenin türünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, sembol sağlayıcıları tarafından, çalışma zamanında belirlenebileceği herhangi bir tür için temel sınıf olarak uygulanır. Bu yalnızca yönetilen kod içindir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, daha fazla özelleştirilmiş arabirimlerin türetilebilecek temel bir sınıfı temsil eder.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim öğesinden Devralınanlar dışında herhangi bir yöntem sağlamaz `IDebugField` .

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
