---
description: Sunucu için kolay bir ad alır.
title: 'IDebugCoreServer3:: GetServerFriendlyName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72e281c6e40f8aea558ef600b531e59a3b26a5c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094139"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Sunucu için kolay bir ad alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametreler
`pbstrName`\
dışı Sunucu için kolay bir ad döndürür.

> [!NOTE]
> Çağıran, dizeyi boşaltmaktan sorumludur.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı tarafından başlatılan sunucular için, bu yöntemin döndürdüğü ad sunucunun tam adıdır. Otomatik başlatılan sunucular için, ad sunucunun üzerinde çalıştığı makinenin adıdır.

 Makineye yönelik bir ad için [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) metodunu çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
