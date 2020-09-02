---
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700672"
---
# <a name="sccgetversion-function"></a>SccGetVersion İşlevi
Bu işlev, kaynak denetimi eklentisi tarafından desteklenen kaynak denetimi eklentisi API 'sinin sürüm numarasını alır.

## <a name="syntax"></a>Söz dizimi

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 `LONG`Desteklenen kaynak denetimi EKLENTISI API 'sinin sürüm numarasını içeren bir veri türü:

|WORD|Description|
|----------|-----------------|
|HıWORD|Ana sürüm|
|LOWORD|İkincil sürüm|

## <a name="remarks"></a>Açıklamalar
 Örneğin, kaynak denetimi eklentisi kaynak denetimi eklentisi API 'sinin 1,3 sürümünü destekliyorsa, bu işlev 0x0103 ' ü döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
