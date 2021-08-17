---
description: IDiaSymbol::findInlineFramesByVA, bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçeveler arasında devamını sağlayan bir sabit adı alır.
title: IDiaSymbol::findInlineFramesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 54295d3e-bbb6-4c10-ab9d-adcfc22b1f71
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 98a591428c0ae33bf3fc07bacd1da1f75bb7280bcb69665d6991aa1b52b23516
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454818"
---
# <a name="idiasymbolfindinlineframesbyva"></a>IDiaSymbol::findInlineFramesByVA
Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçeveler üzerinde devamını sağlayan bir sabit adı alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findInlineFramesByVA ( 
   ULONGLONG         va,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `va`

[in] Adresi VA olarak belirtir.

 `ppResult`

[out] Alınan `IDiaEnumSymbols` çerçevelerin listesini içeren bir nesneyi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
