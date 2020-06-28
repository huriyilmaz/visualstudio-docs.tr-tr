---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe609d53571e6ffcd8e18919f0351e29c0329b46
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465365"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
İki sembolün eşdeğer olup olmadığını denetler.

## <a name="syntax"></a>Söz dizimi

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

'ndaki `IDiaSymbol`Karşılaştırmada kullanılan ikinci nesne.

## <a name="return-value"></a>Dönüş Değeri
 Semboller eşdeğer ise, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` simgeler eşdeğer değildir. Aksi takdirde, bir hata kodu döndürün.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)