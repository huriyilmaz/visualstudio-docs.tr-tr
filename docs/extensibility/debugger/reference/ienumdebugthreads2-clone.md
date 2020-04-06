---
title: IEnumDebugThreads2::Klon | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 239a7d55eadd15845d40dccc2c395ec90d3b4106
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715230"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
Geçerli numaralandırmanın bir kopyasını ayrı bir nesne olarak döndürür.

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
[çıkış] Bu numaralandırmanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralandırmanın kopyası, bu yöntemin çağrıldığı anda orijinalle aynı duruma sahiptir. Ancak, kopyanın ve orijinalin durumları ayrıdır ve ayrı ayrı değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
