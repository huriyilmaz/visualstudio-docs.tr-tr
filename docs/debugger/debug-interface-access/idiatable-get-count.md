---
title: 'IDiaTable:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get_Count method
ms.assetid: bb47abe8-6706-4679-bc52-79f6444dae7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c48db236e7cd416929d26d3473c537c2d81ac06
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461333"
---
# <a name="idiatableget_count"></a>IDiaTable::get_Count
Tablodaki öğelerin sayısını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Tablodaki öğe sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)