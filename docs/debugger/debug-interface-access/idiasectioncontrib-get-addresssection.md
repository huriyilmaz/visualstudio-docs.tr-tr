---
description: Katkı adresinin bölüm bölümünü alın.
title: IDiaSectionContrib::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_addressSection method
ms.assetid: 13fe7e0b-c978-4a1d-bb57-64c8583b5e14
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d549d9ef101cb5b94f19c70e1b5a0c9f1860e964
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161592"
---
# <a name="idiasectioncontribget_addresssection"></a>IDiaSectionContrib::get_addressSection
Katkı adresinin bölüm bölümünü alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Katkı adresinin bölüm bölümünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu `S_FALSE` özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
