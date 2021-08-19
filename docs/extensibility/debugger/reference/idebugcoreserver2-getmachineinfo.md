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
ms.openlocfilehash: 3f9372e921bbd804c7867928a9090fb6b5aae27e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127395"
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
