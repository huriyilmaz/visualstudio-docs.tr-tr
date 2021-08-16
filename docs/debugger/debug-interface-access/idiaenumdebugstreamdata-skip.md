---
description: Numaralandırılmış bir dizide belirtilen sayıda kaydı atlar.
title: 'IDiaEnumDebugStreamData:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5fed50813441176454ae52d7c72847207a1ec78d4b9deb2505ab9ded94f98b1b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380617"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
Numaralandırılmış bir dizide belirtilen sayıda kaydı atlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametreler
 celt

'ndaki Numaralandırılmış dizide atlanacak kayıt sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, öğesini döndürür `S_OK` ; Aksi takdirde, `S_FALSE` atlanacak daha fazla kayıt yoksa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
