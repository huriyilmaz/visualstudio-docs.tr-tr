---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729874"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Hata ayıklama altyapısının (DE), yürütme devam ettiğinde hata ayıklamakta olan programa bu özel durumu geçirme seçeneğini destekleyip desteklemediğini belirler.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Dönüş Değeri
 Ya `S_OK` (özel durum programa geçirilebilir) veya `S_FALSE` (özel durum geçirilemez) döndürür.

## <a name="remarks"></a>Açıklamalar
 Aynı hata ayıklananın geçirilmesi için bir varsayılan eyleme sahip olmalıdır. IDE, [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) olayını alabilir ve yöntemi çağırılmadan [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodunu çağırabilir `CanPassToDebuggee` . Bu nedenle, özel durumu geçirmek için DE varsayılan bir durum olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
