---
title: 'IEnumDebugObjects:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39f2949a0c3b0c7009b17c8ceee09eee210c61cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957107"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Bu yöntem, numaralandırmayı ilk öğe olarak sıfırlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra [Next 'e sonraki](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) çağrı, numaralandırmanın ilk öğesini döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
