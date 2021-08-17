---
description: ', Eşleşen ilk bağlamın bir dizinini döndürürken, belirtilen dizide bulunan her bir bağlamla bellek bağlamını karşılaştırır.'
title: 'IDebugMemoryContext2:: Compare | Microsoft Docs'
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
ms.openlocfilehash: dbf7260bfa0119bf4ffe4ba9ea06c1a59e76fdbaa83d54a3696fdf9d3e34c894
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342173"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
, Eşleşen ilk bağlamın bir dizinini döndürürken, belirtilen dizide bulunan her bir bağlamla bellek bağlamını karşılaştırır.

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
'ndaki [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) numaralandırmasından karşılaştırma türünü belirleyen bir değer.

`rgpMemoryContextSet`\
'ndaki Karşılaştırılacak [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnelerine başvuru dizisi.

`dwMemoryContextSetLen`\
'ndaki Dizideki bağlamların sayısı `rgpMemoryContextSet` .

`pdwMemoryContext`\
dışı Karşılaştırmayı karşılayan ilk bellek bağlamının dizinini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_COMPARE_CANNOT_COMPARE`İki bağlamlar karşılaştırılamamışsa döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklama altyapısının (de) tüm karşılaştırma türlerini desteklemesi gerekmez, ancak en az `CONTEXT_EQUAL` , ve ' ı desteklemesi gerekir `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
