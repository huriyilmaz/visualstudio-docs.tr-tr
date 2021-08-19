---
description: Kaynak kodu baytlarını alır.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bd210d3d4130d94193abec38c41bda7bce67eaaa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044601"
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

dışı Döndürülen baytları temsil eden bayt sayısını döndürür. `data`İse `NULL` , `pcbData` kullanılabilir toplam veri baytı sayısıdır.

 `data[]`

dışı Kaynak baytlarıyla doldurulacak bir arabellek.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
