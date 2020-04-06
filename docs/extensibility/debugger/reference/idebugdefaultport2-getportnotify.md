---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732410"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Bu yöntem, bu bağlantı noktası için bir [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) arabirimi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parametreler
`ppPortNotify`\
[çıkış] Bir [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Normalde, `QueryInterface` yöntem bir [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) arabirimi elde etmek için [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimini uygulayan nesneye çağrılır. Ancak, istenilen arabirimfarklı bir nesne üzerinde uygulandığı durumlar vardır. Bu yöntem bu durumları gizler ve `IDebugPortNotify2` arabirimi en uygun nesneden döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
