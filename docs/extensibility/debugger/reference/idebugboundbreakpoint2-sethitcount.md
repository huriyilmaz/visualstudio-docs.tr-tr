---
description: Bağlı kesme noktası için isabet sayısını ayarlar.
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fcc979118c4bb82327fe6bfcab76d3ca0d11b48
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127512"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Bağlı kesme noktası için isabet sayısını ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>Parametreler
`dwHitCount`\
[in] Ayar için isabet sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Bağlı kesme noktası nesnesinin durumu olarak `E_BP_DELETED` ayarlanmışsa döndürür `BPS_DELETED` (BP_STATE bir parçası). [](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Açıklamalar
 Isabet sayısı, bu kesme noktası oturumun geçerli çalıştırması sırasında kaç kez çalıştırılacağıdır.

 Bu yöntem genellikle hata ayıklama altyapısı tarafından bu kesme noktası üzerinde geçerli isabet sayısını güncelleştirmek için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
