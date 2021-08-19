---
description: Verilen bir konumdan başlayarak bayt dizisini okur.
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6715129ad449e7d92ed2b74785469408973b25c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043446"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Verilen bir konumdan başlayarak bayt dizisini okur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Parametreler
`pStartContext`\
[in] Baytları okumaya nereden başlayacağını belirten [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi.

`dwCount`\
[in] Okunan bayt sayısı. Ayrıca dizinin uzunluğunu `rgbMemory` belirtir.

`rgbMemory`\
[in, out] Gerçekte okunan baytlarla doldurulmuş dizi.

`pdwRead`\
[out] Aslında okunan bitişik bayt sayısını döndürür.

`pdwUnreadable`\
[in, out] Okunamaz bayt sayısını döndürür. İstemci okunamaz bayt sayısıyla ilgisizse null değer olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 100 bayt istenen ve ilk 50 okunabilir ise, sonraki 20 okunamaz ve kalan 30 bayt okunabilirse, bu yöntem şunları döndürür:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 Bu durumda, çünkü çağıranın istenen özgün 100 bayt kalan 30 baytı okumak için ek bir çağrı yapmaları gerekir ve parametresinde geçirilen `*pdwRead + *pdwUnreadable < dwCount` [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi 70 kadar gelişmiş `pStartContext` olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
