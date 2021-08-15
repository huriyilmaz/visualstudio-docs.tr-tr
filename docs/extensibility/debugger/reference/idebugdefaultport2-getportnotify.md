---
description: Bu yöntem, bu bağlantı noktası için bir IDebugPortNotify2 arabirimi alır.
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96a8f103a3df275657dc191183873353c7be620f1819e7950a342e5dcf12bcb9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377736"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Bu yöntem, bu bağlantı [noktası için bir IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) arabirimi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parametreler
`ppPortNotify`\
[out] Bir [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Normalde, bir `QueryInterface` [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) arabirimi elde etmek için [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimini uygulayan nesnede yöntemi çağrılır. Ancak, istenen arabirimin farklı bir nesnede uygulanmasına neden olan durumlar vardır. Bu yöntem bu koşulları gizler ve arabirimi `IDebugPortNotify2` en uygun nesneden döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
