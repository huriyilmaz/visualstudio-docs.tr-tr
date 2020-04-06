---
title: IDebugEngineProgram2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730306"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Bu arabirim, çok iş parçacığı hata ayıklama desteği sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı, birden çok iş parçacığının eşzamanlı hata ayıklamasını desteklemek için bu arabirimi uygular. Bu arabirim, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan aynı nesne üzerinde uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi bir `IDebugProgram2` arabirimden elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugEngineProgram2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Durdur](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Bu programda çalışan tüm iş parçacıklarını durdurur.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Verilen iş parçacığı üzerinde gerçekleşmesi için yürütme (veya yürütme için izlemeyi durdurmak) için saatler.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Program durdurulsa bile, verilen iş parçacığı üzerinde ifade değerlendirmesinin gerçekleşmesine izin verir (veya izin vermese).|

## <a name="remarks"></a>Açıklamalar
 Visual Studio bu arabirimi bir [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) etkinliğine yanıt olarak çağırır ve programın "Thread Step'i izleyin" ve "İplikte İfade Değerlendirmesi Için İzle" durumlarını ayarlamak için çağırır. Program durdurulacak olduğunda [durdurma](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) denir; bu yöntem, programa tüm iş parçacıklarını sonlandırma şansı verir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
