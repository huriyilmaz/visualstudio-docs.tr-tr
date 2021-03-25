---
description: Yürütmenin devam ettiğinde veya özel durumun atıldığında hata ayıklamakta olan programa özel durumun geçirilip geçirilmeyeceğini belirtir.
title: IDebugExceptionEvent2::P Asstodebugayıklanan | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81af5686cfc2b99dc3bf5d95e2ec283933297e2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084772"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Yürütmenin devam ettiğinde veya özel durumun atıldığında hata ayıklamakta olan programa özel durumun geçirilip geçirilmeyeceğini belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parametreler
`fPass`\
'ndaki `TRUE`Özel durumun, yürütme devam ettiğinde hata ayıklamakta olan programa geçirilmesi gerekiyorsa sıfır olmayan () veya `FALSE` özel durumun atılmalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin çağrılması, aslında hata ayıklamakta olan programda hiçbir kodun yürütülmesine neden olmaz. Çağrı yalnızca sonraki kod yürütmesinin durumunu ayarlamak içindir. Örneğin, [Canpasstodebugayıklanan](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) metoduna yapılan çağrılar `S_OK` [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)döndürebilir.`dwState` alan olarak ayarlanır `EXCEPTION_STOP_SECOND_CHANCE` .

 IDE [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) olayını alabilir ve [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) metodunu çağırabilir. Hata ayıklama altyapısının (DE), yöntem çağrılmaması durumunda durumu işlemek için varsayılan bir davranışı olmalıdır `PassToDebuggee` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Devam et](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
