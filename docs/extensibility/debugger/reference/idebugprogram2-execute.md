---
title: IDebugProgram2::Yürüt | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722986"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Bu programı durmuş durumdaki bir durumdan çalıştırmaya devam ediyor. Önceki yürütme durumu (adım gibi) temizlenir ve program yeniden yürütmeye başlar.

> [!NOTE]
> Bu yöntem amortismana hazırdır. Bunun yerine [Yürüt](../../../extensibility/debugger/reference/idebugprocess3-execute.md) yöntemini kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı başka bir programın iş parçacığı nda durdurulmuş bir durumdan yürütme başladığında, bu yöntem bu programda çağrılır. Kullanıcı IDE'deki **Hata Ayıklama** menüsünden **Başlat** komutunu seçtiğinde bu yöntem de çağrılır. Bu yöntemin uygulanması, programdaki geçerli iş parçacığı üzerinde [Devam](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemini aramak kadar basit olabilir.

> [!WARNING]
> Bu aramayı işlerken Bir durdurma olayını veya [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) anına anında (eşzamanlı) bir olay göndermeyin; aksi takdirde hata ayıklama asılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)
