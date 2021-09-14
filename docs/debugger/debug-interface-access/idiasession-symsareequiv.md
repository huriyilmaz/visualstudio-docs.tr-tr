---
description: İki sembolün eşdeğer olup olmadığını denetler.
title: 'IDiaSession:: Symsareequıv | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2483a201da07fe45247e3ad0c389d969e2657772
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629066"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
İki sembolün eşdeğer olup olmadığını denetler.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parametreler
 `symbolA`

'ndaki Karşılaştırmada kullanılan ilk [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi.

 `symbolB`

'ndaki `IDiaSymbol` Karşılaştırmada kullanılan ikinci nesne.

## <a name="return-value"></a>Dönüş Değeri
 Semboller eşdeğer ise, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` simgeler eşdeğer değildir. Aksi takdirde, bir hata kodu döndürün.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
