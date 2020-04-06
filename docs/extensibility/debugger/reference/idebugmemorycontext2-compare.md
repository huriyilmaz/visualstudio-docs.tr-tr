---
title: IDebugMemoryContext2::Karşılaştır | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727497"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Bellek bağlamını, verilen dizideki her bağlamla karşılaştırma bayraklarıyla gösterilen şekilde karşılaştırır ve eşleşen ilk bağlamın dizinini döndürer.

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
[içinde] Karşılaştırma türünü belirleyen [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) numaralandırma değeri.

`rgpMemoryContextSet`\
[içinde] Karşılaştırılması gereken [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnelerine yapılan bir dizi başvuru.

`dwMemoryContextSetLen`\
[içinde] `rgpMemoryContextSet` Dizideki bağlam ların sayısı.

`pdwMemoryContext`\
[çıkış] Karşılaştırmayı tatmin eden ilk bellek bağlamının dizinini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. İki `E_COMPARE_CANNOT_COMPARE` bağlam karşılaştırılamıyorsa döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı (DE) karşılaştırmalar her türlü desteklemek zorunda değildir, `CONTEXT_EQUAL` `CONTEXT_LESS_THAN`ancak `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE`en az desteklemesi gerekir , , ve .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
