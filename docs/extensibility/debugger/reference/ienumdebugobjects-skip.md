---
title: IEnumDebugObjects::Atla | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80d2ae53ea7732a2120cf0431f33f929a0a6bc05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716278"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
Bu yöntem, belirtilen öğe sayısını atlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[içinde] Atlasılayacak öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. Kalan `S_FALSE` `celt` öğelerin sayısından büyükse döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalan `celt` öğelerin sayısından daha büyük bir değer belirtirse, numaralandırma sonuna `S_FALSE` ayarlanır ve döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
