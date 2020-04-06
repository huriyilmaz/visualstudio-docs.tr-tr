---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733142"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Bu yöntem, bir sunucu için makine yardımcı programları alır.

> [!NOTE]
> Bu yöntem eskidir: kullanmayın[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] (bu `E_NOTIMPL` yöntem çağrılırsa her zaman döndürür). Tarihsel nedenlerden dolayı korunur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametreler
`ppUtil`\
[çıkış] Makine `IDebugMDMUtil2_V7` yardımcı programları bilgilerini temsil eden bir arabirim döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her `E_NOTIMPL`zaman döndürür , yöntemin uygulanmadığını gösterir.

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]bu `E_NOTIMPL` yöntem çağrılırsa her zaman döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
