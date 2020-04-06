---
title: IDebugCanStopEvent2::GetReason | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734528"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Hata ayıklama altyapısının (DE) durdurmak istemesinin nedenini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>Parametreler
`pcr`\
[çıkış] Bu olayın nedenini açıklayan [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) numaralandırmadan bir değer verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem genellikle [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) yönteminden önce çağrılır, böylece arayan`TRUE` `IDebugCanStopEvent2::CanStop` yönteme sıfırsız () geçip geçmeyeceğini belirleyebilir.

 Durdurma nedeni, `CANSTOP_ENTRYPOINT`DE'nin bir giriş noktasına ulaştığı anlamına `CANSTOP_STEPIN`gelir veya DE'nin bir işleve adım attığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
