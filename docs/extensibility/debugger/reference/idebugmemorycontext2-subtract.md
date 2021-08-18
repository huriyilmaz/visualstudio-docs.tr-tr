---
description: Belirtilen değeri geçerli bağlamdan çıkarır ve yeni bir bağlam döndürür.
title: IDebugMemoryContext2::Subtract | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b25e58fed406863009b72220fad4ba04b0d3b1e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118677"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Belirtilen değeri geçerli bağlamdan çıkarır ve yeni bir bağlam döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametreler
`dwCount`\
[in] Azalarak kaç bellek baytı olduğunu.

`ppMemCxt`\
[out] Yeni bir [IDebugMemoryContext2 nesnesi](../../../extensibility/debugger/reference/idebugmemorycontext2.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bellek bağlamı bir adrestir, bu nedenle bir adresten değer çıkararak yeni bir bağlam arabirimi gerektiren yeni bir adres üretir.

 Sonuçta elde edilen adres bu bağlamla ilişkili bellek alanı dışında olsa bile bu yöntem her zaman yeni bir bağlam üretmektedir. Bunun tek istisnası, yeni bağlam için bellek ayırılamayacak olması veya null değer `ppMemCxt` olmasıdır (bu bir hatadır).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
