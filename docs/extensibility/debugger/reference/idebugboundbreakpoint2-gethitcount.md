---
description: Bu bağlantılı kesme noktası için geçerli isabet sayısını alır.
title: 'IDebugBoundBreakpoint2:: GetHitCount | Microsoft Docs'
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
ms.openlocfilehash: 8bc2fa014bb3ac8f58d61206c5bd828e0570c2ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079928"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
Bu bağlantılı kesme noktası için geçerli isabet sayısını alır.

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
dışı İsabet sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. , `E_BP_DELETED` Bağlantılı kesme noktası nesnesinin durumunun `BPS_DELETED` ( [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) sabit listesinin parçası) olarak ayarlanmış olup olmadığını döndürür.

## <a name="remarks"></a>Açıklamalar
 İsabet sayısı, bu kesme noktasının, oturumun geçerli çalıştırması sırasında kaç kez tetiklenme sayısıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
