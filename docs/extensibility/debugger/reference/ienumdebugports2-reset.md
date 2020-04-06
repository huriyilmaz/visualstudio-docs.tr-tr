---
title: IEnumDebugPorts2::Sıfırlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6247e48af98f5c21a0afc40577e18d38bba06506
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716187"
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
Numaralandırmayı ilk öğeye sıfırlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra, [Sonraki](../../../extensibility/debugger/reference/ienumdebugports2-next.md) yönteme bir sonraki çağrı numaralandırmanın ilk öğesini döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
