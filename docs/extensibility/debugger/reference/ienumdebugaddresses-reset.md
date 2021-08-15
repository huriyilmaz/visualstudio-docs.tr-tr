---
description: Bu yöntem, adres sabit listesini ilk öğe olarak sıfırlar.
title: 'IEnumDebugAddresses:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42d53d2d3af1853c42c51f5d990102d0db951ba81fa0c7ad6dd6d1f6e0b8981d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415523"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
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
 Bu yöntem çağrıldıktan sonra [Next 'e sonraki](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) çağrı, numaralandırmanın ilk öğesini döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
