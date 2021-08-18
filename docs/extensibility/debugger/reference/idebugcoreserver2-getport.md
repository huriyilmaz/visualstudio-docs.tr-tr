---
description: Belirli bir bağlantı noktasını alın.
title: IDebugCoreServer2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6abc9a9b003a5829b0cc7d7809cb4f63c432513
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072291"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Belirli bir bağlantı noktasını alın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parametreler
`guidPort`\
[in] Alınan bağlantı noktasının GUID'si.

`ppPort`\
[out] İstenen bağlantı [noktasını temsil eden bir IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Verilen `E_PORTSUPPLIER_NO_PORT` tanımlayıcıya sahip bir bağlantı noktası yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
