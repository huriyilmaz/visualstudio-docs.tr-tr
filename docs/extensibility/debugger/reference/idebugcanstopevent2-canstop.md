---
title: IDebugCanStopEvent2::CanStop | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734597"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Hata ayıklama altyapısına (DE) geçerli kod konumunda durup durmayacağını veya yürütmeye devam edip etmeyeceğini bildirin.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parametreler
`fCanStop`\
[içinde] Sıfır sız`TRUE`( ) DE geçerli kod konumunda durmalıdır; aksi takdirde,`FALSE`sıfır ( ).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu olayın alıcısı genellikle DE'nin durdurmak isteme nedenini belirlemek için [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) `IDebugCanStopEvent2::CanStop` yöntemini çağırır ve ardından yöntemi uygun yanıtla çağırır.

 DE durursa, durdurma nedenini açıklayan bir olay gönderir. Gönderilen genellikle iki olay vardır, [iDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) arabirimi tarafından temsil edilen bir kullanıcı veya sinyal sonu ve [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) arabirimi tarafından temsil edilen bir kesme noktası olayı.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
