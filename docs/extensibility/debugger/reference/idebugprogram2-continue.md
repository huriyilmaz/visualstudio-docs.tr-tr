---
title: IDebugProgram2::Devam | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723068"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Bu programı durmuş durumdaki bir durumdan çalıştırmaya devam ediyor. Önceki yürütme durumu (adım gibi) korunur ve program yeniden yürütmeye başlar.

> [!NOTE]
> Bu yöntem amortismana hazırdır. Bunun yerine [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) yöntemini kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametreler
`pThread`[içinde] İş parçacığı temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, kaç programın debugged olduğuna veya hangi programın durdurma olayı nın oluşturulduğuna bakılmaksızın bu programda çağrılır. Uygulama önceki yürütme durumunu (adım gibi) tutmalı ve önceki yürütmeyi tamamlamadan önce hiç durmamış gibi yürütmeye devam etmelidir. Diğer bir deyişle, bu programdaki bir iş parçacığı bir adım-over işlemi yapıyorsa ve başka bir program durdurulduğu için durdurulduysa ve sonra bu yöntem çağrıldıysa, programın özgün adım tamamlama işlemini tamamlaması gerekir.

> [!WARNING]
> Bu aramayı işlerken Bir durdurma olayını veya [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) anına anında (eşzamanlı) bir olay göndermeyin; aksi takdirde hata ayıklama asılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
