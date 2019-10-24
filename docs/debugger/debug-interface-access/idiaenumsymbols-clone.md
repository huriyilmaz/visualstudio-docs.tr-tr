---
title: 'IDiaEnumSymbols:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 07e3823a62ca6fdb81fa6916eec6a1de5598a748
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743982"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>Parametreler
 ppEnum

dışı Numaralandırıcının yinelemesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür. Semboller yinelenmez, yalnızca Numaralandırıcı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)