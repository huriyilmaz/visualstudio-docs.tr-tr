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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2c712652cbdb84b987e898a44c97779e0ff5417b32cf69cd88dffe64792219db
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455074"
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
