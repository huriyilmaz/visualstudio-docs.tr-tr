---
title: 'IDiaSession:: Symsareequıv | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741863"
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

'ndaki Karşılaştırmada kullanılan ikinci `IDiaSymbol` nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Semboller eşdeğer ise `S_OK`döndürür; Aksi takdirde, `S_FALSE`döndürür, semboller eşit değildir. Aksi takdirde, bir hata kodu döndürün.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)