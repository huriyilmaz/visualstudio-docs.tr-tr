---
description: Geçerli iş parçacıklarının bir kopyasını ayrı bir nesne olarak döndürür.
title: IEnumDebugThreads2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a229bd68ffd0ce0c9c699a8db43dfc48f85b3a9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152672"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
Geçerli numaralamanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Clone(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
[out] Bu numaralamanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralamanın kopyası, bu yöntemin çağrıldı olduğu sırada özgün ile aynı durumla aynıdır. Ancak kopyaların ve özgünlerin durumları ayrıdır ve tek tek değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
