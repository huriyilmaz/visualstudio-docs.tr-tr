---
description: Bu yöntem, kullanıcının güvenli olmayan bir işleme iliştirmadan önce bağlantı noktası sağlayıcısı 'nın bir uyarı görüntülemesine olanak tanır.
title: 'Idebugprocesssecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e6a586983d64e8be27b15a0514234d1a321e943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166170"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Bu yöntem, kullanıcının güvenli olmayan bir işleme iliştirmadan önce bağlantı noktası sağlayıcısı 'nın bir uyarı görüntülemesine olanak tanır.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Dönüş Değeri
 Dönüş değerleri aşağıdaki gibidir:

- `S_OK`: İşleme ekleme güvenlidir ve hiçbir uyarı iletişim kutusu gösterilmez.

- `S_FALSE`: Ekleme bir güvenlik sorunu ve uyarı içeren bir iletişim kutusu gösterilir.

- `FAILURE`: İşleme ekleme başarısız oluyor.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
