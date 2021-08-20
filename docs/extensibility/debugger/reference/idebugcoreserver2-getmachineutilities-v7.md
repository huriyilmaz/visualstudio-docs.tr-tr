---
description: Bu yöntem, bir sunucunun makine yardımcı programlarını alır.
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca461fe31d29cde2bd11031923bf31c3d262ff08
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064532"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Bu yöntem, bir sunucunun makine yardımcı programlarını alır.

> [!NOTE]
> Bu yöntem kullanımdan kalkmıştır: kullanma ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] bu yöntem `E_NOTIMPL` çağrılsa her zaman döndürür). Bu, geçmiş nedenlerden dolayı korunur.

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
[out] Makine yardımcı `IDebugMDMUtil2_V7` program bilgilerini temsil eden bir arabirim döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Yönteminin `E_NOTIMPL` uygulanmadığını gösteren her zaman döndürür.

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] bu yöntem `E_NOTIMPL` çağrılsa her zaman döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
