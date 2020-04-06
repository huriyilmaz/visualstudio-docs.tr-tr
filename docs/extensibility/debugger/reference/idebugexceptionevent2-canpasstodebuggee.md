---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729874"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Hata ayıklama altyapısının (DE) yürütme devam ettiğinde hata ayıklama programına bu özel durumu geçirme seçeneğini destekleyip desteklemediğini belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Dönüş Değeri
 İade `S_OK` eder ya (özel durum programa `S_FALSE` geçirilebilir) veya (özel durum geçirilemez).

## <a name="remarks"></a>Açıklamalar
 DE hata ayıklama geçmek için varsayılan bir eylem olmalıdır. [IDE, IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) olayını alabilir ve yöntemi aramadan `CanPassToDebuggee` [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) yöntemini arayabilir. Bu nedenle, DE özel durum veya geçiş için varsayılan bir durumda olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Devam](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
