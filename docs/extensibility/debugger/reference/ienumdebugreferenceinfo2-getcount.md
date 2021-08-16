---
description: Numaralamada DEBUG_REFERENCE_INFO öğe sayısını döndürür.
title: IEnumDebugReferenceInfo2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::GetCount
helpviewer_keywords:
- IEnumDebugReferenceInfo2::GetCount
ms.assetid: e62706e0-d2cd-48fb-8fdf-444463c651ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f22197625989a3fbc74852729fc2166778da0d92decc17c70c8b81746e5183df
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377254"
---
# <a name="ienumdebugreferenceinfo2getcount"></a>IEnumDebugReferenceInfo2::GetCount
Numaralamada öğe sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametreler
`pcelt`\
[out] Numaralamada öğe sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yalnızca , , ve yöntemlerinin uygulanmasının gerekli olduğunu belirten özel COM numaralama `Next` `Clone` `Skip` `Reset` arabiriminin bir parçası değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
