---
title: IDebugMemoryContext2::Çıkarma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727442"
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
[içinde] Kararnameye ait bellek baytlarının sayısı.

`ppMemCxt`\
[çıkış] Yeni bir [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bellek bağlamı bir adrestir, bu nedenle bir adresten değer çıkarmak yeni bir bağlam arabirimi gerektiren yeni bir adres üretir.

 Bu yöntem, ortaya çıkan adres bu bağlamla ilişkili bellek alanının dışında olsa bile, her zaman yeni bir bağlam oluşturmalıdır. Bunun tek istisnası, yeni bağlam için bellek ayrılamazsa `ppMemCxt` veya null bir değerse (bir hatadır).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
