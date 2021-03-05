---
description: Tüm kullanılabilir bağlantı noktalarının listesini alır.
title: 'IDebugCoreServer2:: TRTs | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::EnumPorts
helpviewer_keywords:
- IDebugCoreServer2::EnumPorts
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9da125b5e10315f74d806cf5ba7026601393366
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154762"
---
# <a name="idebugcoreserver2enumports"></a>IDebugCoreServer2::EnumPorts
Tüm kullanılabilir bağlantı noktalarının listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumPorts( 
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPorts( 
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı Tüm bağlantı noktası tedarikçilerinin tüm bağlantı noktalarının listesini içeren bir [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
