---
description: Bu yöntem, geçerli alan numaralamalarının bir kopyasını ayrı bir nesne olarak döndürür.
title: IEnumDebugFields::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2c1e8e0003b9c6ded698b2da56c5a0dcb2ee1ef172060cfa3bc427a73e1faa2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389195"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Bu yöntem, geçerli numaralamanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
[out] Bu numaralamanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralamanın kopyası, bu yöntemin çağrıldı olduğu sırada özgün ile aynı durumla aynıdır. Ancak kopyaların ve özgünlerin durumları ayrıdır ve tek tek değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
