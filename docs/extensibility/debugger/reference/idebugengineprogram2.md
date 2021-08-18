---
description: Bu arabirim çok iş parçacıklı hata ayıklama desteği sağlar.
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8c2660c430ac18f337c61275297eb385216904cf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035156"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Bu arabirim çok iş parçacıklı hata ayıklama desteği sağlar.

## <a name="syntax"></a>Syntax

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir hata ayıklama altyapısı, bu arabirimi birden çok iş parçacığının eşzamanlı hata ayıklamasını desteklemek için uygular. Bu arabirim, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan aynı nesne üzerinde uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi bir arabirimden almak için [QueryInterface](/cpp/atl/queryinterface) kullanın `IDebugProgram2` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugEngineProgram2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Durdur](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Bu programda çalışan tüm iş parçacıklarını sonlandırır.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Verilen iş parçacığında yürütmeyi izler (veya yürütmeyi İzlemeyi Durdur).|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Program durdurulmuş olsa bile, belirtilen iş parçacığında ifade değerlendirmesinin yapılmasına izin verir (veya izin vermez).|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, bu arabirimi bir [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olayına yanıt olarak çağırır ve programın "iş parçacığı adımını izle" ve "iş parçacığında ifade değerlendirmesini izle" durumlarını ayarlamak için. [Durdur](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) , program her durdurulduğunda çağrılır; Bu yöntem programa tüm iş parçacıklarını sonlandırma şansı verir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
