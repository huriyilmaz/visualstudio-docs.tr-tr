---
description: Bu işlev, kaynak denetimi eklentisi tarafından desteklenen kaynak denetimi eklentisi API 'sinin sürüm numarasını alır.
title: SccGetVersion Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f49d33ebe70390a364d0ae8336e7f69549b6876f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901090"
---
# <a name="sccgetversion-function"></a>SccGetVersion İşlevi
Bu işlev, kaynak denetimi eklentisi tarafından desteklenen kaynak denetimi eklentisi API 'sinin sürüm numarasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 `LONG`Desteklenen kaynak denetimi EKLENTISI API 'sinin sürüm numarasını içeren bir veri türü:

|WORD|Açıklama|
|----------|-----------------|
|HıWORD|Ana sürüm|
|LOWORD|İkincil sürüm|

## <a name="remarks"></a>Açıklamalar
 Örneğin, kaynak denetimi eklentisi kaynak denetimi eklentisi API 'sinin 1,3 sürümünü destekliyorsa, bu işlev 0x0103 ' ü döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
