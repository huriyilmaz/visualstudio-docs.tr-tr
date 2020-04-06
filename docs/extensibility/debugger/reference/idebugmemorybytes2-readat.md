---
title: IDebugMemoryBytes2::ReadAt | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727538"
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
[içinde] Baytokumaya nereden başlayacağını belirten [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi.

`dwCount`\
[içinde] Okunacak bayt sayısı. Ayrıca `rgbMemory` dizinin uzunluğunu belirtir.

`rgbMemory`\
[içinde, dışarı] Dizi baytlar ile dolu aslında okuyun.

`pdwRead`\
[çıkış] Fiilen okunan bitişik bayt sayısını verir.

`pdwUnreadable`\
[içinde, dışarı] Okunamayan bayt sayısını verir. İstemci okunamayan bayt sayısıyla ilgilenmiyorsa, null bir değer olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 100 bayt isteniyorsa ve ilk 50 okunabilirise, sonraki 20'si okunamazsa ve geri kalan 30'u okunabilirse, bu yöntem döndürür:

 *`pdwRead`= 50

 *`pdwUnreadable`= 20

 Bu durumda, `*pdwRead + *pdwUnreadable < dwCount`çünkü , arayan orijinal 100 istenen kalan 30 bayt okumak için ek bir arama yapmak gerekir ve `pStartContext` parametre geçirilen [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi 70 tarafından ilerletilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
