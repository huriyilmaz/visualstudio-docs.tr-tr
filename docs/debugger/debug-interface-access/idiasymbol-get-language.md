---
title: 'IDiaSymbol:: get_language | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e7dc0a0a640a9d3921801a9077b32ade5921ff7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463122"
---
# <a name="idiasymbolget_language"></a>IDiaSymbol::get_language
Kaynağın dilini alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT get_language ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Kaynak dilini belirten [CV_CFL_LANG numaralandırma](../../debugger/debug-interface-access/cv-cfl-lang.md) numaralandırmasından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CV_CFL_LANG Numaralandırması](../../debugger/debug-interface-access/cv-cfl-lang.md)