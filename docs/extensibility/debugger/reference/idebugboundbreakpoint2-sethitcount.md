---
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e82f12b12c9afbc24f9416ec2639a4b9768d8fd0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735410"
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
[içinde] Vuruş sayısı ayarlı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Bağlı `E_BP_DELETED` kesme noktası nesnesinin durumu `BPS_DELETED` ayarlanmışsa [(BP_STATE](../../../extensibility/debugger/reference/bp-state.md) numaralandırmanın bir parçası) döndürür.

## <a name="remarks"></a>Açıklamalar
 Isabet sayısı, bu kesme noktasının oturumun geçerli çalışması sırasında kaç kez ateşettiğidir.

 Bu yöntem genellikle hata ayıklama altyapısı tarafından bu kesme noktasında geçerli isabet sayısını güncelleştirmek için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
