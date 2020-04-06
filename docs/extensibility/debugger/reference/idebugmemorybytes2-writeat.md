---
title: IDebugMemoryBytes2::WriteAt | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727523"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Belirtilen adresten başlayarak belirtilen bellek bayt sayısını yazar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parametreler
`pStartContext`\
[içinde] Bayt yazmaya nereden başlayacağını belirten [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi.

`dwCount`\
[içinde] Yazacak bayt sayısı.

`rgbMemory`\
[içinde] Yazıya baytlar. Bu dizinin en `dwCount` azından bayt boyutu olduğu varsayılır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, tüm baytlar yazılabilir veya bir hata `E_FAIL`kodu döndürebilir (genellikle) döndürür. `S_FALSE`

## <a name="remarks"></a>Açıklamalar
 Başlangıç adresi bu [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) nesnesi tarafından temsil edilen bellek penceresinde değilse, yazma `E_FAIL` miktarı bellek alanına çakışsa bile hiçbir yazı oluşur ve bir hata kodu döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
