---
description: Sunucunun adını verir.
title: IDebugCoreServer3::GetServerName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerName
helpviewer_keywords:
- IDebugCoreServer3::GetServerName
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eddf2260b3b518fd411f649feba37d6b8e0830a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111469"
---
# <a name="idebugcoreserver3getservername"></a>IDebugCoreServer3::GetServerName
Sunucunun adını verir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetServerName(
   BSTR* pbstrName
);
```

```csharp
int GetServerName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametreler
`pbstrName`\
[out] Sunucunun adını döndürür.

> [!NOTE]
> Çağıran, dizeyi serbest bırakarak sorumludur.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kolay bir sunucu adı için [GetServerFriendlyName yöntemini](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)
