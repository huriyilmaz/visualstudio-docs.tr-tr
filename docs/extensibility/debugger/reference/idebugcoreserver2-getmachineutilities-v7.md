---
description: Bu yöntem, bir sunucu için makine yardımcı programlarını alır.
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26d2c042c6f4a08acb7efc558bbc86021b16587e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077960"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Bu yöntem, bir sunucu için makine yardımcı programlarını alır.

> [!NOTE]
> Bu yöntem artık kullanılmıyor: kullanmayın ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `E_NOTIMPL` Bu yöntem çağrılırsa her zaman döner). Bu, geçmiş nedenlerle tutulur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametreler
`ppUtil`\
dışı `IDebugMDMUtil2_V7` Makine yardımcı programları bilgilerini temsil eden bir arabirim döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` , yöntemin uygulanmadığını belirten ' i döndürür.

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]`E_NOTIMPL`Bu yöntem çağrılırsa her zaman döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
