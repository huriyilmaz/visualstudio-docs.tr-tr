---
description: Compiland'ın) /LTCG (Bağlantı Zamanı Kod Oluşturma)(/cpp/build/reference/ltcg-link-time-code-generation) ile bağlanıp bağlanıp bağlana olmadığını belirten bir bayrağını alın. Bu da program iyileştirmesi konusunda yardımcı olur.
title: IDiaSymbol::get_isLTCG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0c7b73b33739ade2b83b5e9e2ae760845de1d7e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121508"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
[Compiland'ın](../../debugger/debug-interface-access/compiland.md) tüm program iyileştirmeye yardımcı olan [/LTCG (Bağlantı](/cpp/build/reference/ltcg-link-time-code-generation)Zamanı Kod Oluşturma) anahtarla bağlantılı olup olmadığını belirten bir bayrak alınır. Bu anahtar yalnızca yönetilen kod için geçerlidir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 pFlag

[out] , `TRUE` `compiland` /LTCG bağlantı anahtarıyla bağlantılı ise döndürür; aksi takdirde `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> dönüş `S_FALSE` değeri, özelliğin sembol için kullanılamaz olduğu anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üstbilgi:|dia2.h|
|Sürüm:|DIA SDK v8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
