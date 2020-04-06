---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723203"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Bu yöntem, bağlantı noktası tedarikçisinin kullanıcı güvenli olmayan bir işleme bağlanmadan önce bir uyarı görüntülemesine olanak tanır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Dönüş Değeri
 İade değerleri aşağıdaki gibidir:

- `S_OK`: İşleme takmak güvenlidir ve hiçbir uyarı iletişim kutusu gösterilmez.

- `S_FALSE`: Takmak bir güvenlik sorunu olabilir ve uyarı içeren bir iletişim kutusu gösterilir.

- `FAILURE`: İşleme bağlanmak başarısız olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
