---
description: Bu yöntem, geçerli adresler numaralamanın bir kopyasını ayrı bir nesne olarak döndürür.
title: IEnumDebugAddresses::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88c87c56daa16ef146c9397b252dee2779092018
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125705"
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
Bu yöntem, geçerli numaralamanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Clone(
   IEnumDebugAddresses** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugAddresses ppEnum
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
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
