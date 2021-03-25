---
description: Bu yöntem, kullanıcının güvenli olmayan bir işleme iliştirmadan önce bağlantı noktası sağlayıcısı 'nın bir uyarı görüntülemesine olanak tanır.
title: 'Idebugprocesssecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbbfcf11a35fcfc43ae9e903b13a7480a3cf9743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076283"
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
