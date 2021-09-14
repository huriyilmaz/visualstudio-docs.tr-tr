---
description: Bu arabirim, hata ayıklama altyapısı (DE) tarafından bir işlevden çıkıp işlevin üzerinden adımlama sonrasında oturum hata ayıklama yöneticisine (SDM) gönderilir.
title: IDebugReturnValueEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8fb0c74c955ba27590916e3b48f801db4f6dc9ec
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725792"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından bir işlevden çıkıp işlevin üzerinden adımlama sonrasında oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugReturnValueEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bu arabirimi kullanarak veya tekrar atmış olan bir işlevden dönüş değerini raporlar. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak gerçekleştir gerekir. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE işlevin dönüş değerini rapor etmek için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklama yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemini `IDebugReturnValueEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|bir işlevden dışarı adımlamada döndürülen değeri alır.|

## <a name="remarks"></a>Açıklamalar
 Bir işlev tarafından döndürülen değer [GetReturnValue çağrılarak elde edilir.](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) Döndürülen değer Otomatikler **penceresinde** görünür.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
