---
description: Bu bağlantı noktası için bağlantı noktası tedarikçiyi alır.
title: 'IDebugPort2:: Getporttedarikçi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 7a7b0615-df6b-4726-ab35-39dfa1ebed8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2bf426b59f835c9b450751bb06b779d657ac807
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142849"
---
# <a name="idebugport2getportsupplier"></a>IDebugPort2::GetPortSupplier
Bu bağlantı noktası için bağlantı noktası tedarikçiyi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPortSupplier( 
   IDebugPortSupplier2** ppSupplier
);
```

```csharp
int GetPortSupplier( 
   out IDebugPortSupplier2 ppSupplier
);
```

## <a name="parameters"></a>Parametreler
`ppSupplier`\
dışı Bir bağlantı noktası için bağlantı noktası tedarikçiyi temsil eden bir [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
