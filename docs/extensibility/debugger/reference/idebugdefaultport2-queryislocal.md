---
description: Bu yöntem, bu bağlantı noktasının yerel makinede olup olmadığını belirler.
title: 'IDebugDefaultPort2:: Queryıslocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f732de2526aa71698b4c01a636dab541050015a5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150646"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Bu yöntem, bu bağlantı noktasının yerel makinede olup olmadığını belirler.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Dönüş Değeri
 `S_OK`Bu bağlantı noktasının yerel olup olmadığını (çağıranın bulunduğu makinede) veya `S_FALSE` bağlantı noktasının başka bir makine üzerinde olup olmadığını döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
