---
description: Simgenin alt öğelerini alır. Döndürülen yerel semboller, program iyileştirme ile derlenmişse canlı Aralık bilgilerini içerir.
title: 'IDiaSymbol:: findChildrenEx | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c23788815590f5122191cc3db7190cfb9581e1c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091131"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Simgenin alt öğelerini alır. Döndürülen yerel semboller, program iyileştirme ile derlenmişse canlı Aralık bilgilerini içerir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findChildrenEx ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `symtag`

'ndaki [SymTagEnum numaralandırmasında](../../debugger/debug-interface-access/symtagenum.md)tanımlandığı şekilde alınacak alt öğelerin sembol etiketlerini belirtir. `SymTagNull`Tüm alt öğelerin alınması için olarak ayarlayın.

 `name`

'ndaki Alınacak alt öğelerin adını belirtir. `NULL`Tüm alt öğelerin alınması için olarak ayarlayın.

 `compareFlags`

'ndaki Ad eşleştirme için uygulanacak karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.

 `ppResult`

dışı Alınan alt simgelerin listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 `S_OK`Simgenin en az bir alt öğesi bulunursa veya `S_FALSE` alt öğe bulunmazsa öğesini döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [IDiaSymbol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)'ın genişletilmiş sürümüdür.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)
