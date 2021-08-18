---
description: Bir sınıf üyesinin erişim değiştiricisini alın.
title: IDiaSymbol::get_access | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_access method
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 71ed7ca5018e69541d254750f5e7c4956cded569
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081328"
---
# <a name="idiasymbolget_access"></a>IDiaSymbol::get_access
Bir sınıf üyesinin erişim değiştiricisini alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_access ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Sınıf üyesinin [erişim değiştiricisini belirten](../../debugger/debug-interface-access/cv-access-e.md) CV_access_e enumeration enumeration'dan bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v7.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CV_access_e Numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)
