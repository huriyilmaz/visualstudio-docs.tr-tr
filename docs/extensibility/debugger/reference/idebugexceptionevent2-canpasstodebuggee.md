---
description: Hata ayıklama altyapısının (DE) bu özel durumu yürütme devam ettirilen programda hata ayıklandı seçeneğine geçirme seçeneğini destekleyip desteklemeyip desteklemeyeceklerini belirler.
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6741866b2b056792ea58d03bdd3abd6ed0f28d1d532ff2b5070b1f3cbe8af5c0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292591"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Hata ayıklama altyapısının (DE) bu özel durumu yürütme devam ettirilen programda hata ayıklandı seçeneğine geçirme seçeneğini destekleyip desteklemeyip desteklemeyeceklerini belirler.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Dönüş Değeri
 (Özel `S_OK` durum programa geçir olabilir) veya `S_FALSE` (özel durum geçirilemiyor) döndürür.

## <a name="remarks"></a>Açıklamalar
 DE'nin hata ayıklayıcıya geçiş için varsayılan bir eylemi olması gerekir. IDE, [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) olayını alır ve yöntemini çağırmadan [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) yöntemini `CanPassToDebuggee` çağırmış olabilir. Bu nedenle, DE'nin özel durumu geçirme veya geçirme için varsayılan bir durumu olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
