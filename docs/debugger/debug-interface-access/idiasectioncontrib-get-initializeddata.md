---
title: 'IDiaSectionContrib:: get_initializedData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_initializedData method
ms.assetid: f5c108be-a0cc-408b-9590-b8d44361810c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae43ee519f0c0d03be9697b4361f6ff939d2b411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466261"
---
# <a name="idiasectioncontribget_initializeddata"></a>IDiaSectionContrib::get_initializedData
Bölümün başlatılmış verileri içerip içermediğini gösteren bir bayrak alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_initializedData ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı `TRUE` Bölüm başlatılmış verileri içeriyorsa döndürür; Aksi takdirde, döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)