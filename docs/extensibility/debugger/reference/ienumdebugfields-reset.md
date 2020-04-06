---
title: IEnumDebugFields::Sıfırlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be33249ef583776f613c6716143249e3ce31bc8d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716858"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Bu yöntem, ilk öğeye numaralandırmayı sıfırlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Parametreler
 None

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra, [Sonraki](../../../extensibility/debugger/reference/ienumdebugfields-next.md) çağrı numaralandırmanın ilk öğesini döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Sonraki](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
