---
description: Hata ayıklama altyapısının (DE) durdurulması nedenini alır.
title: 'IDebugCanStopEvent2:: GetReason | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66b783044b8342de26aec831d9d41f8bccd7df92
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173530"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Hata ayıklama altyapısının (DE) durdurulması nedenini alır.

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
dışı Bu olayın nedenini açıklayan [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) numaralandırmasından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem genellikle [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) yönteminden önce çağrılır, böylece çağıranın sıfır olmayan () yönteme geçirilip geçemeyeceğini belirleyebilmesini sağlayabilirsiniz `TRUE` `IDebugCanStopEvent2::CanStop` .

 Durdurma nedeni, ya da bir `CANSTOP_ENTRYPOINT` giriş noktasına eriştiği anlamına gelir, yanı `CANSTOP_STEPIN` de bir işlev olarak da çalışır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
