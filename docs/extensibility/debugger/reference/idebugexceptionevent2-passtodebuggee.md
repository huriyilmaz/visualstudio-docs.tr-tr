---
title: IDebugExceptionEvent2::P Asstodebugayıklanan | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729836"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Yürütmenin devam ettiğinde veya özel durumun atıldığında hata ayıklamakta olan programa özel durumun geçirilip geçirilmeyeceğini belirtir.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
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
