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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4de4b0c30b697f96c65250b89002abdfccafa20a0cfe14f1267a537ad2b7841
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377781"
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
