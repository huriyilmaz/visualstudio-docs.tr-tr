---
description: Bu programda çalışan tüm iş parçacıklarını sonlandırır.
title: 'IDebugEngineProgram2:: durdur | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7263756a0a8bacbbc6f90e327916cec8868d8f5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077375"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Bu programda çalışan tüm iş parçacıklarını sonlandırır.

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
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bu programın bir çoklu program ortamında hata ayıklaması yapıldığında çağrılır. Başka bir programdan durdurulan bir olay alındığında bu yöntem bu programda çağırılır. Bu yöntemin uygulanması zaman uyumsuz olmalıdır; Yani, bu yöntemin döndürüldüğünden önce tüm iş parçacıklarının durdurulması gerekmez. Bu yöntemin uygulanması, bu programda [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) yöntemini çağırmak kadar basit olabilir.

 Program durdurulduğunda uygulayıcılar bir [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) göndermelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
