---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2526fd4991677eca60b908d6ab1f4b3e6e8189af
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467199"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
Derleyiciye özgü çerçeve türünü alır.

## <a name="syntax"></a>Söz dizimi

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