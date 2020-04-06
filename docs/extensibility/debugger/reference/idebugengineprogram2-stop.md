---
title: IDebugEngineProgram2::Stop | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730489"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Bu programda çalışan tüm iş parçacıklarını durdurur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu program çok programlı bir ortamda debugged ediliyor bu yöntem denir. Başka bir programdan durdurma olayı alındığı zaman, bu yöntem bu programda çağrılır. Bu yöntemin uygulanması asynchronous olmalıdır; diğer bir diğer olarak, bu yöntem dönmeden önce tüm iş parçacıklarının durdurulması gerekmez. Bu yöntemin uygulanması, bu programda [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) yöntemini aramak kadar basit olabilir.

 Program durduğunda uygulayıcılar bir [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) göndermelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
