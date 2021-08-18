---
description: Hata ayıklama altyapısı (DE), yürütülmektedir olan programda bir özel durum thrown olduğunda bu arabirimi oturum hata ayıklama yöneticisine (SDM) gönderir.
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9a76ee7facb47a76e7d3887c8eb391f076769edb51a9ace6b62899fe57e29e79
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433937"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Hata ayıklama altyapısı (DE), yürütülmektedir olan programda bir özel durum thrown olduğunda bu arabirimi oturum hata ayıklama yöneticisine (SDM) gönderir.

## <a name="syntax"></a>Syntax

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, hata ayıklaması yapılan programda bir özel durum olduğunu rapor etmek için bu arabirimini uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak uygulanarak. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE bu olay nesnesini oluşturur ve bir özel durum bildirmeye gönderir. Olay, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugExceptionEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Bu olayı neden olan özel durum hakkında ayrıntılı bilgi alır.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Bu olayı neden olan özel durum için okunabilir bir açıklama alır.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Hata ayıklama altyapısının (DE) bu özel durumu yürütme devam ettirilen programda hata ayıklandı seçeneğine geçirme seçeneğini destekleyip desteklemeyip desteklemeyeceklerini belirler.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Yürütme devam ettirilen programda özel durumun hata ayıklamaya geçirip geçirilemayacak veya özel durumun atılacak olup olmadığını belirtir.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Açıklamalar
 Olay göndermeden önce DE, bu özel durum olayına [önceki bir SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)çağrısı tarafından birinci şans veya ikinci şans özel durumu atanarak atanma olup ola bir denetim oluşturur. Birinci şans özel durumu olarak belirlenmişse, `IDebugExceptionEvent2` olay SDM'ye gönderilir. Yoksa, DE uygulamaya özel durumu işleme şansı verir. Bir özel durum işleyicisi sağlanıyorsa ve özel durum ikinci şans özel durumu olarak belirlenmişse, `IDebugExceptionEvent2` olay SDM'ye gönderilir. Aksi takdirde, DE programın yürütülmesini sürdürür ve işletim sistemi veya çalışma zamanı özel durumu ele almaktadır.

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
