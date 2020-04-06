---
title: IDebugPortSupplier2::CanAddPort | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724752"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Bağlantı noktası tedarikçisinin yeni bağlantı noktaları ekleyebileceğini doğrular.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Dönüş Değeri
 Bağlantı noktası eklenebiliyorsa, geri döner; `S_OK` aksi takdirde, bu bağlantı noktası tedarikçisine bağlantı noktası eklenmediğini belirtmek için iadeler. `S_FALSE`

## <a name="remarks"></a>Açıklamalar
 İkinci yöntem bağlantı noktasını oluşturduğundan ve zaman alan bir işlem olabilecek eklediğinden, [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) yöntemini çağırmadan önce bu yöntemi arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
