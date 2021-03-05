---
description: Özellik değerinin bellek bağlamını alır.
title: 'IDebugProperty2:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a82b2f0ed4a1fb7a37ec621d737d624d30d33ef2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166859"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
Özellik değerinin bellek bağlamını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext(
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>Parametreler
`ppMemory`\
dışı Bu özellikle ilişkili belleği temsil eden [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT`Alınacak bellek bağlamı yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
