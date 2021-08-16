---
description: Çekirdek sunucunun üzerinde çalıştığı makinenin açıklamasını alır.
title: 'IDebugCoreServer2:: Getmachineınfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetInfo
helpviewer_keywords:
- IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38fde9a0bfed0a915cdb4ea16e95d04597931c8c13975b866adce95dde4e2ac4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377840"
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
Çekirdek sunucunun üzerinde çalıştığı makinenin açıklamasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMachineInfo( 
   MACHINE_INFO_FIELDS Fields,
   MACHINE_INFO*       pMachineInfo
);
```

```csharp
int GetMachineInfo( 
   enum_ MACHINE_INFO_FIELDS  Fields,
   MACHINE_INFO[]             pMachineInfo
);
```

## <a name="parameters"></a>Parametreler
`Fields`\
'ndaki [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi `pMachineInfo` .

 `pMachineInfo`\

 [in, out] Makinenin açıklamasıyla doldurulmuş bir [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
