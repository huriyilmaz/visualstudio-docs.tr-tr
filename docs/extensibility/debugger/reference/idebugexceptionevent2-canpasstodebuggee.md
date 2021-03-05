---
description: Hata ayıklama altyapısının (DE), yürütme devam ettiğinde hata ayıklamakta olan programa bu özel durumu geçirme seçeneğini destekleyip desteklemediğini belirler.
title: 'IDebugExceptionEvent2:: Canpasstodebugayıklanan | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152890"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Hata ayıklama altyapısının (DE), yürütme devam ettiğinde hata ayıklamakta olan programa bu özel durumu geçirme seçeneğini destekleyip desteklemediğini belirler.

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
 Ya `S_OK` (özel durum programa geçirilebilir) veya `S_FALSE` (özel durum geçirilemez) döndürür.

## <a name="remarks"></a>Açıklamalar
 Aynı hata ayıklananın geçirilmesi için bir varsayılan eyleme sahip olmalıdır. IDE, [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) olayını alabilir ve yöntemi çağırılmadan [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodunu çağırabilir `CanPassToDebuggee` . Bu nedenle, özel durumu geçirmek için DE varsayılan bir durum olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
