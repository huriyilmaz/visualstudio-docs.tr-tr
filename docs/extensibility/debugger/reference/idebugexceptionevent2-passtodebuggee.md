---
description: Özel durumun yürütme devam ettirilen programda hata ayıklamaya geçirip geçirilemayacak veya özel durumun atılacak olup olmadığını belirtir.
title: IDebugExceptionEvent2::P assToDebuggee | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96843835eb1873b6b754f651b853413680981a795e94e97b6aef6cfbd753e5e2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307628"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Özel durumun yürütme devam ettirilen programda hata ayıklamaya geçirip geçirilemayacak veya özel durumun atılacak olup olmadığını belirtir.

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
[in] Yürütme devam ettirilen programda özel durum geçir gerekirse sıfır dışında ( ) veya özel durum atılmalıdırsa sıfır `TRUE` ( `FALSE` ) .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin çağrılmış olması, hata ayıklanabilecek programda herhangi bir kodun yürütülmesinde neden olmaz. Çağrısı yalnızca sonraki kod yürütmesi için durumu ayarlamaktır. Örneğin [CanPassToDebuggee yöntemine](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) yapılan çağrılar, `S_OK` EXCEPTION_INFO. [](../../../extensibility/debugger/reference/exception-info.md)`dwState` alan olarak `EXCEPTION_STOP_SECOND_CHANCE` ayarlanmıştır.

 IDE, [IDebugExceptionEvent2 olayını alır](../../../extensibility/debugger/reference/idebugexceptionevent2.md) ve [Continue yöntemini](../../../extensibility/debugger/reference/idebugprogram2-continue.md) çağırmış olabilir. Yöntem çağrılmasa hata ayıklama altyapısının (DE) durumu işlemek için varsayılan `PassToDebuggee` bir davranışı olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Devam et](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
