---
title: 'IDebugMemoryContext2:: Add | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727476"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Geçerli içeriğe belirtilen değeri ekler ve yeni bir bağlam döndürür.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Geçerli bağlama eklenecek değer.

`ppMemCxt`\
dışı Yeni bir [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bellek bağlamı bir adrestir, bu nedenle bir adrese değer eklemek yeni bir bağlam arabirimi gerektiren yeni bir adres oluşturur.

 Bu yöntem, sonuçta elde edilen adres bu içerikle ilişkili bellek alanının dışında olsa bile her zaman yeni bir bağlam üretmelidir. Bunun tek istisnası, yeni bağlam için bellek ayrılamaz veya `ppMemCxt` null bir değer (bir hatadır) ise olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
