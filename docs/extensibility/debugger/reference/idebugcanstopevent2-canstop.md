---
description: Hata ayıklama altyapısına (DE) geçerli kod konumunda durdurulup durdurulmayacağını bildirir veya yürütmeye devam edin.
title: 'IDebugCanStopEvent2:: CanStop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd575d6bb1afdf296eff6ec3ac3a08a9551618b8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636369"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Hata ayıklama altyapısına (DE) geçerli kod konumunda durdurulup durdurulmayacağını bildirir veya yürütmeye devam edin.

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
'ndaki `TRUE`Geçerli kod konumunda durmalı sıfır olmayan (), aksi takdirde sıfır ( `FALSE` ).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu olayın alıcısı genellikle [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) yöntemini çağırarak, onun durdurmak istediği nedeni tespit edin ve ardından `IDebugCanStopEvent2::CanStop` yöntemi uygun Yanıtla çağırır.

 DE duruyorsa, durdurma nedenini açıklayan bir olay gönderir. Tipik olarak gönderilen iki olay, [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) arabirimi tarafından temsil edilen bir kullanıcı veya sinyal kesmesi ve [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) arabirimi tarafından temsil edilen bir kesme noktası olayı vardır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
