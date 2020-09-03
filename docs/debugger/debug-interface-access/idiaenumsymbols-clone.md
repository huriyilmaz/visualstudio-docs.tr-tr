---
title: 'IDiaEnumSymbols:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4621c25daf8b8c8415f84eb87f06e7223ff30cf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467801"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>Parametreler
 ppEnum

dışı Numaralandırıcının yinelemesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür. Semboller yinelenmez, yalnızca Numaralandırıcı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)