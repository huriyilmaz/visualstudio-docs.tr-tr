---
description: Bağlantılı kesme noktası için isabet sayısını ayarlar.
title: 'IDebugBoundBreakpoint2:: SetHitCount | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63284fea43c283ad291e0207946fe6f5d36f5a4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095777"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Bağlantılı kesme noktası için isabet sayısını ayarlar.

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
'ndaki Ayarlanacak isabet sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. , `E_BP_DELETED` Bağlantılı kesme noktası nesnesinin durumunun `BPS_DELETED` ( [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) sabit listesinin parçası) olarak ayarlanmış olup olmadığını döndürür.

## <a name="remarks"></a>Açıklamalar
 İsabet sayısı, bu kesme noktasının, oturumun geçerli çalıştırması sırasında kaç kez tetiklenme sayısıdır.

 Bu yöntem, bu kesme noktasında geçerli isabet sayısını güncelleştirmek için genellikle hata ayıklama altyapısı tarafından çağırılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
