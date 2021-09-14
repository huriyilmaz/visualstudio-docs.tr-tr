---
description: Bellek bağlamını, bayrakları karşılaştırarak belirtilen şekilde verilen dizide yer alan her bağlamla karşılaştırarak eşleşen ilk bağlamın dizinini döndürür.
title: IDebugMemoryContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b0e4e55872da333089d91eddd8edb54d7ce99f5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627387"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Bellek bağlamını, bayrakları karşılaştırarak belirtilen şekilde verilen dizide yer alan her bağlamla karşılaştırarak eşleşen ilk bağlamın dizinini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Parametreler
`compare`\
[in] Karşılaştırma türünü [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) bir değerdir.

`rgpMemoryContextSet`\
[in] Karşılaştırma yapılacak [IDebugMemoryContext2 nesnelerine](../../../extensibility/debugger/reference/idebugmemorycontext2.md) yönelik başvuru dizisi.

`dwMemoryContextSetLen`\
[in] Dizide bağlam `rgpMemoryContextSet` sayısı.

`pdwMemoryContext`\
[out] Karşılaştırmayı yerine getiren ilk bellek bağlamının dizinini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. İki `E_COMPARE_CANNOT_COMPARE` bağlam karşılaştırılayamasa döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısının (DE) tüm karşılaştırma türlerini desteklemesi gerek değildir, ancak en azından `CONTEXT_EQUAL` , ve 'i `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` desteklemesi `CONTEXT_SAME_SCOPE` gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
