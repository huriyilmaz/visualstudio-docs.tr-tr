---
description: Bu yöntem, bu bağlantı noktasının açık olduğu sunucuya bir arabirim edinir.
title: 'IDebugDefaultPort2:: GetServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d5bfd242cd3f441bf094f94e41a78e240f1ec46
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162985"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Bu yöntem, bu bağlantı noktasının açık olduğu sunucuya bir arabirim edinir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Parametreler
`ppServer`\
dışı [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) arabirimini uygulayan bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) , Visual Studio tarafından uygulanır ve bağlantı noktasının bulunduğu sunucuyu temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
