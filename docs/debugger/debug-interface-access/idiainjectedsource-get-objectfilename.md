---
title: 'IDiaInjectedSource:: get_objectFilename | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_objectFilename method
ms.assetid: 7c42847a-f0df-443a-a9fe-c495c1271ea8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f223acd5d6f62417b8a47889aa4e9e4a116335c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467059"
---
# <a name="idiainjectedsourceget_objectfilename"></a>IDiaInjectedSource::get_objectFilename
Kaynağın derlendiği nesne dosya adını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_objectFilename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Kaynağın derlendiği nesne dosyası adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)