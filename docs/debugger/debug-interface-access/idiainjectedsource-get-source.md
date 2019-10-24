---
title: 'IDiaInjectedSource:: get_source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b389df8220766ffbdbf865a2b8e70877fe91b3f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743331"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Kaynak kodu baytlarını alır.

## <a name="syntax"></a>Sözdizimi

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

dışı Döndürülen baytları temsil eden bayt sayısını döndürür. @No__t_0 `NULL`, `pcbData` toplam kullanılabilir veri baytı sayısıdır.

 `data[]`

dışı Kaynak baytlarıyla doldurulacak bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu özellik desteklenmiyorsa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)