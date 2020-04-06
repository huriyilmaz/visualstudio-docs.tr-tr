---
title: SccGetVersion Fonksiyonu | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700672"
---
# <a name="sccgetversion-function"></a>SccGetVersion İşlevi
Bu işlev, kaynak denetim eklentisi tarafından desteklenen Kaynak Denetim Eklentisi API'sinin sürüm numarasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 Desteklenen `LONG` Kaynak Denetimi Eklentisi API'sinin sürüm numarasını içeren bir veri türü:

|WORD|Açıklama|
|----------|-----------------|
|HIWORD|Ana sürüm|
|LOWORD|Küçük sürüm|

## <a name="remarks"></a>Açıklamalar
 Örneğin, bir kaynak denetim eklentisi Kaynak Denetim Eklentisi API sürümü 1.3 destekler, bu işlev 0x0103 döndürecek.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
