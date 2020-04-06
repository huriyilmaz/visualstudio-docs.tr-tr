---
title: IDebugExceptionEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729784"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Hata ayıklama altyapısı (DE), şu anda yürütülmekte olan programa bir özel durum atıldığında bu arabirimi oturum hata ayıklama yöneticisine (SDM) gönderir.

## <a name="syntax"></a>Sözdizimi

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, debugged olan programda bir özel durum oluştuğunu bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir özel durum bildirmek için bu olay nesnesini oluşturur ve gönderir. Olay, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugExceptionEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Bu olayı ateşleyen özel durum hakkında ayrıntılı bilgi alır.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Bu olayı ateşleyen istisna için insan tarafından okunabilir bir açıklama alır.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Hata ayıklama altyapısının (DE) yürütme devam ettiğinde hata ayıklama programına bu özel durumu geçirme seçeneğini destekleyip desteklemediğini belirler.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Özel durum, yürütme devam ederken çıkarılan programa geçirilip geçirilmeyeceğini veya özel durum atılıp atılmayacağını belirtir.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Açıklamalar
 Olayı göndermeden önce, DE bu özel durum [olayının SetException'a](../../../extensibility/debugger/reference/idebugengine2-setexception.md)önceki bir çağrıda ilk şans veya ikinci şans özel durumu olarak atanıp atanmamalarını denetler. İlk şans istisnası olarak belirlenmişse, `IDebugExceptionEvent2` olay SDM'ye gönderilir. Değilse, DE uygulama özel durumu işlemek için bir şans verir. Özel durum işleyicisi sağlanmışsa ve özel durum ikinci şans `IDebugExceptionEvent2` özel durumu olarak belirlenmişse, olay SDM'ye gönderilir. Aksi takdirde, DE programın yürütülmesidevam eder ve işletim sistemi veya çalışma zamanı özel durum işler.

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
