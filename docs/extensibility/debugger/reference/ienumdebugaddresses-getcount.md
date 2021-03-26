---
description: Bu yöntem, adres numaralandırmasındaki öğe sayısını döndürür.
title: 'IEnumDebugAddresses:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 067ede2c848726decf925aa3b7bb2a18a7c5d3b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083173"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
Bu yöntem, Numaralandırmadaki öğe sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametreler
`pcelt`\
dışı Numaralandırmadaki öğe sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yalnızca ileri, kopyalama, atlama ve sıfırlama 'nın uygulanması gerektiğini belirten normal com numaralandırma arabiriminin bir parçası değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
