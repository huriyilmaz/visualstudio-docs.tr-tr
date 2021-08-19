---
description: Belirtilen değeri geçerli bağlama ekler ve yeni bir bağlam döndürür.
title: IDebugMemoryContext2::Add | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d3926b151cc078dc879ebbe44ba3b902919bca3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127044"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Belirtilen değeri geçerli bağlama ekler ve yeni bir bağlam döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametreler
`dwCount`\
[in] Geçerli bağlama eklemek için değer.

`ppMemCxt`\
[out] Yeni bir [IDebugMemoryContext2 nesnesi](../../../extensibility/debugger/reference/idebugmemorycontext2.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bellek bağlamı bir adrestir, bu nedenle adrese değer eklemek yeni bağlam arabirimi gerektiren yeni bir adres üretir.

 Sonuçta elde edilen adres bu bağlamla ilişkili bellek alanı dışında olsa bile bu yöntem her zaman yeni bir bağlam üretmektedir. Bunun tek istisnası, yeni bağlam için bellek ayırılamayacak olması veya null değer `ppMemCxt` olmasıdır (bu bir hatadır).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
