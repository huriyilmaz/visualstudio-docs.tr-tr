---
description: Belirtilen adresten başlayarak belirtilen sayıda belleği yazar.
title: 'IDebugMemoryBytes2:: WriteAt | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc1b5547290712f07cd51a935627182ddd12d31c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165156"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Belirtilen adresten başlayarak belirtilen sayıda belleği yazar.

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
'ndaki Baytların yazma başlangıcını belirten [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi.

`dwCount`\
'ndaki Yazılacak bayt sayısı.

`rgbMemory`\
'ndaki Yazılacak bayt sayısı. Bu dizinin boyutunun en az bayt olduğu varsayılır `dwCount` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` tüm baytlar yazılamaz veya bir hata kodu (genellikle) döndürüp döndürmemelidir `E_FAIL` .

## <a name="remarks"></a>Açıklamalar
 Başlangıç adresi bu [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) nesnesi tarafından temsil edilen bellek penceresinde değilse yazma işlemi yapılmaz ve `E_FAIL` yazma miktarı bellek alanına örtüşse bile hata kodu döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
