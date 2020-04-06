---
title: IDebugProcess3::Devam | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723775"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Bu işlemi durdurulan bir durumdan çalıştırmaya devam ediyor. Önceki yürütme durumu (adım gibi) korunur ve işlem yeniden yürütmeye başlar.

> [!NOTE]
> Bu yöntem [Devam yerine](../../../extensibility/debugger/reference/idebugprogram2-continue.md)kullanılmalıdır.

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
`pThread`\
[içinde] Devam edilecek iş parçacığı temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, kaç işlemin debugged veya hangi işlem durdurma olayı oluşturulan ne olursa olsun bu işlem denir. Uygulama önceki yürütme durumunu (adım gibi) tutmalı ve önceki yürütmeyi tamamlamadan önce hiç durmamış gibi yürütmeye devam etmelidir. Diğer bir deyişle, bu işlemdeki bir iş parçacığı bir adım-over işlemi yapıyorsa ve başka bir işlem durdurulduğu için durdurulduysa ve sonra `Continue` çağrıldıysa, belirtilen iş parçacığının özgün adım tamamlama işlemini tamamlaması gerekir.

 **Uyarı** Bu aramayı işlerken Bir durdurma olayını veya [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) anına anında (eşzamanlı) bir olay göndermeyin; aksi takdirde hata ayıklama asılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
