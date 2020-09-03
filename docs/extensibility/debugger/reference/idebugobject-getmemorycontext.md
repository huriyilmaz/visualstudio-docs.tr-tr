---
title: 'IDebugObject:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16427685765c1471fba3993743efc204cb99c367
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726663"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Nesnenin değerinin adresini temsil eden bellek bağlamını alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Parametreler
`pContext`\
dışı Nesnenin değerinin adresini temsil eden bir [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen bellek bağlamı, bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi tarafından temsil edilen değerin adresini belirtir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
