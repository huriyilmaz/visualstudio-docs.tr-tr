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
ms.workload:
- vssdk
ms.openlocfilehash: 89e192f61e4cda809e8e6c90106cbe081392a044
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094425"
---
# <a name="idebugaddress"></a>IDebugAddress
Bu arabirim bir öğenin adresini temsil eder. Sembol işleyici tarafından döndürülür.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, bu arabirimi bir nesnenin adresini temsil etmek için uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimde birçok yöntem bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Bir nesneyi ve konumunu açıklayan [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısını alır.|

## <a name="remarks"></a>Açıklamalar
 Sembol sağlayıcısı, bir nesneyi ve belirli bir kapsam içindeki konumunu (örneğin, işlev, yöntem veya sınıf) temsil etmek için bu arabirimi döndürür. Bu arabirim öğesinden döndürülür ve sembol sağlayıcısı ve ifade değerlendiricisi 'nin çeşitli yöntemlerine geçirilir. Normal olarak, sembol sağlayıcısı bu arabirimin içeriğini yorumlamak için gereken tek varlıktır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
