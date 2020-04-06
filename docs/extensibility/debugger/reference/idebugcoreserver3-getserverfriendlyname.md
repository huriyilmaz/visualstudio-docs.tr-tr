---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eec30783041a1240d8f85815c06f4ca60729a484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732890"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Sunucu için uygun bir ad alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametreler
`pbstrName`\
[çıkış] Sunucu için uygun bir ad verir.

> [!NOTE]
> Arayan dize serbest sorumludur.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı tarafından başlatılan sunucular için, bu yöntemle döndürülen ad, sunucunun tam adıdır. Otomatik olarak başlatılan sunucular için, sunucunun üzerinde çalışan makinenin adıdır.

 Makine odaklı bir ad için [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
