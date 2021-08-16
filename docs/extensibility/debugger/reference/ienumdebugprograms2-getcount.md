---
description: Program numaralama öğeleri sayısını döndürür.
title: IEnumDebugPrograms2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::GetCount
helpviewer_keywords:
- IEnumDebugPrograms2::GetCount
ms.assetid: 84832982-fa68-4090-a5b7-b233817876b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: affb506f81acc20aec2bac35940fa572be7fd4be52d376d6e0b9037c4a98a059
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360072"
---
# <a name="ienumdebugprograms2getcount"></a>IEnumDebugPrograms2::GetCount
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
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
