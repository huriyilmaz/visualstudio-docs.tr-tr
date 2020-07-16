---
title: 'IDebugProgram2:: Continue | Microsoft Docs'
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
ms.openlocfilehash: ee73ea3a9b65635cf14d4d345bf22de4e9593989
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387089"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Bu programı durdurulmuş bir durumdan çalıştırmaya devam eder. Önceki yürütme durumu (bir adım gibi) korunur ve program yeniden yürütülmeye başlar.

> [!NOTE]
> Bu yöntem kullanım dışıdır. Bunun yerine [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodunu kullanın.

## <a name="syntax"></a>Söz dizimi

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
`pThread`'ndaki İş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, kaç tane program ayıklandığına veya durdurma olayını hangi programın üretdiğine bakılmaksızın bu programda çağrılır. Uygulamanın önceki yürütme durumunu (bir adım gibi) yürütmesi ve yürütülmeye devam etmeden önce hiçbir daha durdurulmamış olsa da yürütmeye devam etmesi gerekir. Diğer bir deyişle, bu programdaki bir iş parçacığı adım adım bir işlem yapıyor ve başka bir program durdurulduğu için durdurulduysa ve bu yöntem çağrıldıysa, program özgün adım adım işlemi tamamlamalıdır.

> [!WARNING]
> Bu çağrıyı gerçekleştirirken [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) için bir durdurma olayı veya anında (zaman uyumlu) olay göndermeyin; Aksi takdirde hata ayıklayıcı yanıt vermeyi durdurabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
