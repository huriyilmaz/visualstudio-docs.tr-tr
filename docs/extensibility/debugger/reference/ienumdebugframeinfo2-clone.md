---
title: 'IEnumDebugFrameInfo2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Clone
helpviewer_keywords:
- IEnumDebugFrameInfo2::Clone
ms.assetid: cdd10489-1772-47e3-815f-a6cfd32a3c60
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 494f8d3d2f6a870f2d0b95a1d152f077f0514055
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967819"
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
