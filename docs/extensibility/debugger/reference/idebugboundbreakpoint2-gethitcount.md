---
description: Bu bağlı kesme noktası için geçerli isabet sayısını alır.
title: IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96c93e4a6006060849bab1daf2c0f2ec7d420590d719817a1acbe0b1d35402ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360670"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
Bu bağlı kesme noktası için geçerli isabet sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetHitCount( 
   DWORD* pdwHitCount
);
```

```csharp
int GetHitCount( 
   out uint pdwHitCount
);
```

## <a name="parameters"></a>Parametreler
`pdwHitCount`\
[out] Isabet sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Bağlı kesme noktası nesnesinin durumu olarak `E_BP_DELETED` ayarlanırsa `BPS_DELETED` (varsayılan değer BP_STATE [](../../../extensibility/debugger/reference/bp-state.md) döndürür.

## <a name="remarks"></a>Açıklamalar
 Isabet sayısı, bu kesme noktası oturumun geçerli çalıştırması sırasında kaç kez çalıştırılacağıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
