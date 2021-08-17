---
description: Bu programda çalışan tüm iş parçacıklarını durdurur.
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 308e3b59c5f1a542c2e0b3e10c573c5990d0f85acf2f6b18aa71af9cd84ccd70
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342225"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Bu programda çalışan tüm iş parçacıklarını durdurur.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bu program çok programlı bir ortamda hata ayıklarken çağrılır. Başka bir programdan durdurma olayı alınca, bu programda bu yöntem çağrılır. Bu yöntemin uygulanması zaman uyumsuz olmalı; diğer bir ifadeyle, bu yöntem geri gelmeden önce tüm iş parçacıklarının durdurulmaları gerekli değildir. Bu yöntemin uygulanması, bu programda [CauseBreak yönteminin çağrılarak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) uygulanması kadar basit olabilir.

 Program durduğunda, [uygulayanların bir IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) göndermesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
