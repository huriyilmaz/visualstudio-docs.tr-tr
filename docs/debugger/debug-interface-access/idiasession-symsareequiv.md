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
ms.workload:
- multiple
ms.openlocfilehash: c5f887b13195bdde133c4bca845291b1255b99ea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156988"
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
