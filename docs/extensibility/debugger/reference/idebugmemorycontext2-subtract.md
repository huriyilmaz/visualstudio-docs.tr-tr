---
description: Geçerli bağlamdan belirtilen değeri çıkartır ve yeni bir bağlam döndürür.
title: 'IDebugMemoryContext2:: Subtract | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1007a50ca42164cfc4e4f58c8d2c877cbba20f5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058592"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Geçerli bağlamdan belirtilen değeri çıkartır ve yeni bir bağlam döndürür.

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
