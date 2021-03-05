---
description: Derleyiciye özgü çerçeve türünü alır.
title: 'IDiaFrameData:: get_type | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c362f6a781d7596c438a3fc2c8d0acfc47f070a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157688"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
Derleyiciye özgü çerçeve türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı , Derleyiciye özgü çerçeve türünü gösteren [StackFrameTypeEnum numaralandırma](../../debugger/debug-interface-access/stackframetypeenum.md) numaralandırmasından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [StackFrameTypeEnum Numaralandırması](../../debugger/debug-interface-access/stackframetypeenum.md)
