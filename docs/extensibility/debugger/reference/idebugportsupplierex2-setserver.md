---
description: Bağlantı noktası sağlayıcısı için çekirdek sunucuyu ayarlar.
title: 'IDebugPortSupplierEx2:: SetServer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2::SetServer
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60136aaf238ade896145d96a62e4fa78ff068460
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145422"
---
# <a name="idebugportsupplierex2setserver"></a>IDebugPortSupplierEx2::SetServer
Bağlantı noktası sağlayıcısı için çekirdek sunucuyu ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetServer(
   IDebugCoreServer2* pServer
);
```

```csharp
int SetServer(
   IDebugCoreServer2 pServer
);
```

## <a name="parameters"></a>Parametreler
`pServer`\
Bağlantı noktası sağlayıcısı için ayarlanacak çekirdek sunucu.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)
