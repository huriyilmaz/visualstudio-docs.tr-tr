---
description: Bu yöntem, bu nesnenin bağlandığı belleği temsil eden bir bellek nesnesi alır.
title: 'IDebugBinder3:: GetMemoryObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ca708c9a6fd80a7a04d8202a73f0bce99102ff1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173980"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Bu yöntem, bu nesnenin bağlandığı belleği temsil eden bir bellek nesnesi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMemoryObject(
   IDebugField*   pField,
   UINT64         uConstant,
   IDebugObject** ppObject
);
```

```csharp
int GetMemoryObject(
   IDebugField      pField,
   long             uConstant,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`pField`\
'ndaki Bellek nesnesinin hangi alana alınacağını belirtir.

`uConstant`\
'ndaki Bir sabit değer için bir bellek adresi veya değeri temsil eder.

`ppObject`\
dışı Bu nesnenin bağlandığı belleği temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
