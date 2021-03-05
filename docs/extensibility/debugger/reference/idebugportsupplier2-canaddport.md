---
description: Bir bağlantı noktası tedarikçinin yeni bağlantı noktaları ekleyebildiğini doğrular.
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c53abba81b02aa6125d4fa25ce16db85579ce5c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142667"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Bir bağlantı noktası tedarikçinin yeni bağlantı noktaları ekleyebildiğini doğrular.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Dönüş Değeri
 Bağlantı noktası eklenebilse `S_OK` ; Aksi takdirde, `S_FALSE` Bu bağlantı noktası sağlayıcısına hiçbir bağlantı noktası eklenemeyeceğini göstermek için döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi, [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) metodunu çağırmadan önce çağırın çünkü ikinci yöntem, bağlantı noktasını ve ekleme işlemini zaman alan bir işlem olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
