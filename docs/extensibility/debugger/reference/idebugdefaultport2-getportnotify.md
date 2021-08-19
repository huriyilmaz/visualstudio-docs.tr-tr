---
description: Bu yöntem, bu bağlantı noktası için bir IDebugPortNotify2 arabirimi alır.
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
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
ms.openlocfilehash: 32af766e0c9894ab5c1be42ef62f83d9c5d56b0a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089335"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Bu yöntem, bu bağlantı noktası için bir [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) arabirimi alır.

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
dışı Bir [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Normalde, `QueryInterface` yöntemi, bir [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) arabirimi elde etmek için [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimini uygulayan nesne üzerinde çağrılır. Ancak, istenen arabirimin farklı bir nesne üzerinde uygulandığı durumlar vardır. Bu yöntem bu koşulları gizler ve `IDebugPortNotify2` en uygun nesneden arabirimi döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
