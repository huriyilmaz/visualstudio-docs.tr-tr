---
title: 'IDebugProgram2:: Step | Microsoft Docs'
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
ms.openlocfilehash: c6a70a96014ebf18984c75df60cfeb75ba0d0577
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387245"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Bir adım gerçekleştirir.

> [!NOTE]
> Bu yöntem kullanım dışıdır. Bunun yerine [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) metodunu kullanın.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Bulanan iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

`sk`\
'ndaki Adım türünü belirten [stepkind](../../../extensibility/debugger/reference/stepkind.md) numaralandırmasındaki bir değer.

`step`\
'ndaki Adım birimini belirten [stepunit](../../../extensibility/debugger/reference/stepunit.md) numaralandırmasındaki bir değer (örneğin, ifadeye veya yönergeye göre).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacıkları arasında herhangi bir iş parçacığı eşitlemesi veya iletişim varsa, belirli bir iş parçacığı adımlarken programdaki diğer iş parçacıklarının çalışması gerekir.

> [!WARNING]
> Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
