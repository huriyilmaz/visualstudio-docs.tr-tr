---
description: Belirtilen adresle başlayarak belirtilen bellek bayt sayısını yazar.
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 099da50a72150d425fca560648df743f1804776f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627405"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Belirtilen adresle başlayarak belirtilen bellek bayt sayısını yazar.

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
[in] Bayt [yazmaya nereden başlayacağını belirten IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnesi.

`dwCount`\
[in] Yazacak bayt sayısı.

`rgbMemory`\
[in] Yazacak bayt sayısı. Bu dizinin boyutu en az bayt `dwCount` olarak kabul edilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde, tüm baytlar yazılamayacaksa `S_FALSE` döndürür veya bir hata kodu döndürür (genellikle `E_FAIL` ).

## <a name="remarks"></a>Açıklamalar
 Başlangıç adresi bu [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) nesnesiyle temsil edilen bellek penceresi içinde yoksa, yazma oluşmaz ve yazma miktarı bellek alanıyla çakışsa bile hata kodu `E_FAIL` döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
