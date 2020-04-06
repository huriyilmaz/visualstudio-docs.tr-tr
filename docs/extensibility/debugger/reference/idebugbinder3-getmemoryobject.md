---
title: IDebugBinder3::GetMemoryObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 154873006091a213e69653d3742b3caa8c25b7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735726"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Bu yöntem, bu nesnenin bağlı olduğu belleği temsil eden bir bellek nesnesi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMemoryObject(
   IDebugField*   pField,
   UINT64         uConstant,
   IDebugObject** ppObject
);
```

```csharp
int GetMemoryObject(
   IDebugField      pField,
   long             uConstant,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`pField`\
[içinde] Bellek nesnesini almak için hangi alanın olduğunu belirtir.

`uConstant`\
[içinde] Sabit bir değer için bellek adresini veya değerini temsil eder.

`ppObject`\
[çıkış] Bu nesnenin bağlı olduğu belleği temsil eden bir [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
