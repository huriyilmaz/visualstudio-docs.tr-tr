---
title: 'IDebugMemoryContext2:: Subtract | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727442"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Geçerli bağlamdan belirtilen değeri çıkartır ve yeni bir bağlam döndürür.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Azaltılacak bellek bayt sayısı.

`ppMemCxt`\
dışı Yeni bir [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bellek bağlamı bir adrestir, bu nedenle bir adresten değeri çıkarmak yeni bir bağlam arabirimi gerektiren yeni bir adres oluşturur.

 Bu yöntem, sonuçta elde edilen adres bu içerikle ilişkili bellek alanının dışında olsa bile her zaman yeni bir bağlam üretmelidir. Bunun tek istisnası, yeni bağlam için bellek ayrılamaz veya `ppMemCxt` null bir değer (bir hatadır) ise olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
