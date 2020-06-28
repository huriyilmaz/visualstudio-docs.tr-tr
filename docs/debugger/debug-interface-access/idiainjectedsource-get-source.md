---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8408145d83b3b78f8392603466980495ab32d24b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467031"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Kaynak kodu baytlarını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametreler
 `cbData`

'ndaki Veri arabelleğinin boyutunu temsil eden bayt sayısı.

 `pcbData`

dışı Döndürülen baytları temsil eden bayt sayısını döndürür. `data`İse `NULL` , `pcbData` kullanılabilir toplam veri baytı sayısıdır.

 `data[]`

dışı Kaynak baytlarıyla doldurulacak bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)