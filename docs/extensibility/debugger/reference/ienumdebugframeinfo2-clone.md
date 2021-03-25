---
description: Geçerli FRAMEıNFO numaralandırmasının bir kopyasını ayrı bir nesne olarak döndürür.
title: 'IEnumDebugFrameInfo2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Clone
helpviewer_keywords:
- IEnumDebugFrameInfo2::Clone
ms.assetid: cdd10489-1772-47e3-815f-a6cfd32a3c60
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfd98e66bd498799c33009064b0a48a25fad2b94
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080092"
---
# <a name="ienumdebugframeinfo2clone"></a>IEnumDebugFrameInfo2::Clone
Geçerli numaralandırmanın ayrı bir nesne olarak kopyasını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Clone(
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı Bu numaralandırmanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralandırmanın kopyası, bu yöntemin çağrılışında orijinal ile aynı duruma sahiptir. Bununla birlikte, kopyanın ve özgün durumlarının durumları ayrıdır ve tek tek değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
