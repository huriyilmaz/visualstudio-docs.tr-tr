---
description: Bağlantı noktasını oluşturmak için daha önce kullanılan bir bağlantı noktasının açıklamasını alır (varsa).
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 084e8bb94356ea4e2cff1fa83e83e7e08b35134e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142875"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Bağlantı noktasını oluşturmak için daha önce kullanılan bir bağlantı noktasının açıklamasını alır (varsa).

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parametreler
`ppRequest`\
dışı Bağlantı noktasını oluşturmak için kullanılan isteği temsil eden bir [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  Bir `E_PORT_NO_REQUEST` bağlantı noktasının bir [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) bağlantı noktası isteği kullanılarak oluşturulup oluşturulmadıysa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
