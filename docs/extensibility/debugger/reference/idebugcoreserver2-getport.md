---
title: 'IDebugCoreServer2:: GetPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d8368ccc159fb31941f975c36d165cd943fb113
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929972"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Belirli bir bağlantı noktasını alır.

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
'ndaki Alınacak bağlantı noktasının GUID 'SI.

`ppPort`\
dışı İstenen bağlantı noktasını temsil eden bir [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_PORTSUPPLIER_NO_PORT`Verilen tanımlayıcıya sahip bir bağlantı noktası yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
