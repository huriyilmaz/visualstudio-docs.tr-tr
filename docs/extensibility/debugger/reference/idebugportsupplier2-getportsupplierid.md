---
title: 'IDebugPortSupplier2:: GetPortSupplierId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f56e412d0312de4b6e9522da24004ca37d522aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724613"
---
# <a name="idebugportsupplier2getportsupplierid"></a>IDebugPortSupplier2::GetPortSupplierId
Bağlantı noktası sağlayıcısı tanımlayıcısını alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetPortSupplierId( 
   GUID* pguidPortSupplier
);
```

```csharp
HRESULT GetPortSupplierId( 
   out Guid pguidPortSupplier
);
```

## <a name="parameters"></a>Parametreler
`pguidPortSupplier`\
dışı Bağlantı noktası tedarikçinin GUID 'sini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
