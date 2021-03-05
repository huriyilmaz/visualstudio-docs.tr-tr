---
description: Bu işlev, kaynak denetimi eklentisi tarafından desteklenen kaynak denetimi eklentisi API 'sinin sürüm numarasını alır.
title: SccGetVersion Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a71d3374ffd65e0e7b9a7b2e654885d84e370a9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220605"
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
