---
title: IDebugPort2::GetPortRequest | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48d39ea10e8425d5449444514489ac4b73c0a3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725337"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Daha önce bağlantı noktasını oluşturmak için kullanılan bir bağlantı noktasının açıklamasını alır (varsa).

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
[çıkış] Bağlantı noktasını oluşturmak için kullanılan isteği temsil eden bir [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.  `E_PORT_NO_REQUEST` [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) bağlantı noktası isteği kullanılarak bir bağlantı noktası oluşturulmazsa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
