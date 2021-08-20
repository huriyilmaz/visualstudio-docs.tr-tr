---
description: Bir bağlantı noktası ekler.
title: IDebugPortSupplier2::AddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 581a805ad525f2cbcda95911b1620e7ccd773dfa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132866"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Bir bağlantı noktası ekler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parametreler
`pRequest`\
[in] Eklenecek bağlantı noktasını açıklayan bir [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) nesnesi.

`ppPort`\
[out] Bağlantı noktasını [temsil eden bir IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem aslında istenen bağlantı noktasını oluşturur ve bağlantı noktası sağlayıcının iç etkin bağlantı noktaları listesine ekler. Olası zaman alıcı gecikmeleri önlemek için [önce CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) yöntemi çağrılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
