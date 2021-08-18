---
description: Bu arabirim bir öğenin adresini temsil eder.
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4626e76d84b49411045578b337085d90ebee3ad5af25562443e6382801a8ac8c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293241"
---
# <a name="idebugaddress"></a>IDebugAddress
Bu arabirim bir öğenin adresini temsil eder. Sembol işleyicisi tarafından döndürülür.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı, bir nesnenin adresini temsil etmek için bu arabirimi kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimde birçok yöntem bu arabirimi geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Bu arabirim aşağıdaki yöntemi kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Bir nesneyi [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) konumunu açıklayan bir nesne yapısı oluşturur.|

## <a name="remarks"></a>Açıklamalar
 Sembol sağlayıcısı bir nesneyi ve belirli bir kapsam içindeki konumunu (örneğin, işlev, yöntem veya sınıf) temsil etmek için bu arabirimi döndürür. Bu arabirim, sembol sağlayıcısının ve ifade değerlendiricinin çeşitli yöntemlerinden döndürülür ve bu yöntemlere geçirilebilir. Normalde sembol sağlayıcısı, bu arabirimin içeriğini yorumlaması gereken tek varlıktır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
