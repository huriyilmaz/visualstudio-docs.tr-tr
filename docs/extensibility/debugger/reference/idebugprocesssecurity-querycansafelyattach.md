---
description: Bu yöntem, kullanıcı güvenli olmayan bir işleme eklemeden önce bağlantı noktası sağlayıcının bir uyarı görüntülemesi için izin verir.
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9ee481bb61f0dde92b3e59cbbc728985d0074cb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087905"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Bu yöntem, kullanıcı güvenli olmayan bir işleme eklemeden önce bağlantı noktası sağlayıcının bir uyarı görüntülemesi için izin verir.

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

- `S_FALSE`: Ekleme bir güvenlik sorunu olabilir ve uyarıyla birlikte bir iletişim kutusu gösterilir.

- `FAILURE`: İşleme ekleme başarısız oluyor.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
