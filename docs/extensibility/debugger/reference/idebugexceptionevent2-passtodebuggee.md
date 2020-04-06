---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729836"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Özel durum, yürütme devam ederken çıkarılan programa geçirilip geçirilmeyeceğini veya özel durum atılıp atılmayacağını belirtir.

## <a name="syntax"></a>Sözdizimi

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
[içinde] Nonzero`TRUE`( ) özel durum yürütme devam ederken debugged programa geçirilmelidir, ya da sıfır (`FALSE`) özel durum atılmalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi çağırmak aslında herhangi bir kodun debugged olan programda yürütülmesine neden olmaz. Arama yalnızca bir sonraki kod yürütme için devlet ayarlamaktır. Örneğin, [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) yöntemine yapılan `S_OK` aramalar [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)ile birlikte geri dönebilir.`dwState` alan olarak `EXCEPTION_STOP_SECOND_CHANCE`ayarlanır.

 [IDE, IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) olayını alabilir ve [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) yöntemini arayabilir. Hata ayıklama altyapısı (DE) `PassToDebuggee` yöntemi çağrılmazsa, servis talebi işlemek için varsayılan bir davranış olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Devam](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
