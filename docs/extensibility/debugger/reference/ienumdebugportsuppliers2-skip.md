---
description: Bağlantı noktası sağlayıcıları numaralamada belirtilen öğe sayısını atlar.
title: IEnumDebugPortSuppliers2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Skip
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Skip
ms.assetid: bd95d7e9-274f-485d-8bf6-865306ae1b81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b259d768f6595db64f337de7d966d5b2a6434d7887fb3d08641b771bf02e4a37
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377333"
---
# <a name="ienumdebugportsuppliers2skip"></a>IEnumDebugPortSuppliers2::Skip
Belirtilen öğe sayısını atlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametreler
`celt`\
[in] Atlan öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. kalan `S_FALSE` `celt` öğe sayısından büyükse döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalan öğe sayısından büyük bir değer belirtirse, en sona ayarlanır `celt` ve `S_FALSE` döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
