---
title: 'IDebugObject:: IsReadOnly | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e7d27e6a437c46d2ee72eb4fd5f79eaa9e912ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953636"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Bu nesnenin salt okunurdur belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parametreler
`pfIsReadOnly`\
dışı `TRUE`Bu nesne salt okunurdur sıfır olmayan () döndürür; Aksi takdirde, sıfır ( `FALSE` ) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Salt okunurdur bir nesne, oluşturulduktan sonra değeri değiştirilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
