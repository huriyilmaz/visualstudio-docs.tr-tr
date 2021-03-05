---
description: Bir bağlantı noktasını kaldırır.
title: 'IDebugPortSupplier2:: RemovePort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb19a46f40e4be06f612afad14356f2e469de364
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172071"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Bir bağlantı noktasını kaldırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT RemovePort( 
   IDebugPort2* pPort
);
```

```csharp
int RemovePort( 
   IDebugPort2 pPort
);
```

## <a name="parameters"></a>Parametreler
`pPort`\
'ndaki Kaldırılacak bağlantı noktasını temsil eden bir [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem bağlantı noktasını bağlantı noktası sağlayıcısının iç etkin bağlantı noktaları listesinden kaldırır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
