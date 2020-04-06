---
title: IDebugProgram2::Adım | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722765"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Bir adım gerçekleştirir.

> [!NOTE]
> Bu yöntem amortismana hazırdır. Bunun yerine [Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md) yöntemini kullanın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parametreler
`pThread`\
[içinde] Adımlanan iş parçacığı temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`sk`\
[içinde] Adım türünü belirten [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) numaralandırmasından bir değer.

`step`\
[içinde] [Stepbirimi](../../../extensibility/debugger/reference/stepunit.md) numaralandırmasından bir değer (örneğin, deyim veya yönergeile) adım birimini belirtir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacıkları arasında iş parçacığı eşitleme veya iletişim olması durumunda, belirli bir iş parçacığı adımlanırken programdaki diğer iş parçacıkları çalıştırılmalıdır.

> [!WARNING]
> Bu aramayı işlerken Bir durdurma olayını veya [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) anına anında (eşzamanlı) bir olay göndermeyin; aksi takdirde hata ayıklama asılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
