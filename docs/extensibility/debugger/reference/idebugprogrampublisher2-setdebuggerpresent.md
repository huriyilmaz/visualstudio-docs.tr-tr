---
description: Program yayımcıya bir hata ayıklayıcının mevcut ve çalışıyor olduğunu söyler.
title: IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23c5c59e738eb49c148a873248cd6eae08f04f14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063999"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Program yayımcıya bir hata ayıklayıcının mevcut ve çalışıyor olduğunu söyler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

## <a name="parameters"></a>Parametreler
`fDebuggerPresent`\
[in] Bir hata `TRUE` ayıklayıcı varsa sıfır olmayan ( ), yoksa sıfır ( ) `FALSE` olur.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklayıcının varlığı veya olmaması [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) yönteminden döndürülen verilere yansıtıldı: döndürülen değer, yöntemine yapılan önceki bir çağrıyla ayarlanır veya `SetDebuggerPresent` temiz olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
