---
description: Bu sınır kesme noktasıyla ilişkili koşulu ayarlar veya değiştirir.
title: IDebugBoundBreakpoint2::SetCondition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c419b081c756af9ec0dd4eafc1c7400af339c96
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111690"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Bu sınır kesme noktasıyla ilişkili koşulu ayarlar veya değiştirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parametreler
`bpCondition`\
[in] Koşulu açıklayan [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Bağlı kesme noktası nesnesinin durumu olarak `E_BP_DELETED` ayarlanırsa `BPS_DELETED` (varsayılan değer BP_STATE [](../../../extensibility/debugger/reference/bp-state.md) döndürür.

## <a name="remarks"></a>Açıklamalar
 Daha önce bu kesme noktasıyla ilişkili tüm koşullar kaybolur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
