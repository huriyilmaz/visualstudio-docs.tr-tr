---
title: 'IDiaSymbol:: findChildren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3c62271f6324e50a68de393cfa668c69ba4a935
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741295"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
Simgenin alt öğelerini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `symtag`

'ndaki [SymTagEnum numaralandırmasında](../../debugger/debug-interface-access/symtagenum.md)tanımlandığı şekilde alınacak alt öğelerin sembol etiketlerini belirtir. Tüm alt öğelerin alınabilmesi için `SymTagNull` olarak ayarlayın.

 `name`

'ndaki Alınacak alt öğelerin adını belirtir. Tüm alt öğelerin alınabilmesi için `NULL` olarak ayarlayın.

 `compareFlags`

'ndaki Ad eşleştirme için uygulanan karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.

 `ppResult`

dışı Alınan alt simgelerin listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Simgenin en az bir alt öğesi bulunursa `S_OK` döndürür veya alt öğe bulunmazsa `S_FALSE` döndürür; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, ilk parametre olarak bu sembolle [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) yöntemini çağırmaya benzer.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)