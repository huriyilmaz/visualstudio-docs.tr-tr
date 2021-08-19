---
description: Bu işlev, kaynak denetimi eklentisi tarafından desteklenen Kaynak Denetimi Eklentisi API'sini sürüm numarasını alır.
title: SccGetVersion İşlev | Microsoft Docs
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3746d249152062d3dc877d0be9dbe6082f2eb8d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110208"
---
# <a name="sccgetversion-function"></a>SccGetVersion İşlevi
Bu işlev, kaynak denetimi eklentisi tarafından desteklenen Kaynak Denetimi Eklentisi API'sini sürüm numarasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 Desteklenen `LONG` Kaynak Denetimi Eklentisi API'sinde sürüm numarasını içeren bir veri türü:

|WORD|Açıklama|
|----------|-----------------|
|HIWORD|Ana sürüm|
|LOWORD|İkincil sürüm|

## <a name="remarks"></a>Açıklamalar
 Örneğin, bir kaynak denetimi eklentisi Kaynak Denetimi Eklentisi API'sini 1.3 sürümünü destekliyorsa, bu işlev 0x0103.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
