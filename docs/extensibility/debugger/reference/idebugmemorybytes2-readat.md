---
title: 'IDebugMemoryBytes2:: ReadAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81a6ce40457243e5492d5c6a44dd5d9dd590920f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909929"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Belirli bir konumdan başlayarak bir bayt dizisini okur.

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
'ndaki Bayt okuma başlangıcını belirten [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi.

`dwCount`\
'ndaki Okunacak bayt sayısı. Ayrıca, dizi uzunluğunu belirtir `rgbMemory` .

`rgbMemory`\
[in, out] Dizi, gerçekten okunan baytlarla doldurulmuştur.

`pdwRead`\
dışı Gerçekten okunan bitişik bayt sayısını döndürür.

`pdwUnreadable`\
[in, out] Okunamayan bayt sayısını döndürür. İstemci okunamaz bayt sayısıyla ilgileniyorsa, null bir değer olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 100 bayt isteniyorsa ve ilk 50 okunabilir ise, sonraki 20 okunamaz ve kalan 30 okunabilir, bu yöntem şunu döndürür:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 Bu durumda, `*pdwRead + *pdwUnreadable < dwCount` çağıranın özgün 100 kalan 30 baytını okumak için ek bir çağrı yapması ve parametreye geçirilen [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesinin `pStartContext` 70 tarafından ileri düzey olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
