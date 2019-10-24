---
title: 'IDiaSymbol:: get_isLTCG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d3fa97d5612b61151d9c435b91f500c87af0b23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740210"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
[Compiland](../../debugger/debug-interface-access/compiland.md) 'ın, tüm program iyileştirmesine yardımcı olan [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation)bağlayıcı anahtarıyla bağlanıp bağlanmadığını belirten bir bayrak alır. Bu anahtar yalnızca yönetilen kod için geçerlidir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametreler
 pFlag

dışı @No__t_1/LTCG bağlayıcı anahtarıyla bağlanmışsa `TRUE` döndürür; Aksi takdirde, `FALSE` döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

> [!NOTE]
> @No__t_0 dönüş değeri, özelliğin simge için kullanılamadığı anlamına gelir.

## <a name="requirements"></a>Gereksinimler

|Gereksinim|Açıklama|
|-----------------|-----------------|
|Üst bilgi|dia2. h|
|Sürüm:|DIA SDK v 8.0|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)