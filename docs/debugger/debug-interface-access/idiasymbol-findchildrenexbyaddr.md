---
description: Belirtilen adreste geçerli olan sembole sahip olan çocuklarına sahip olur.
title: IDiaSymbol::findChildrenExByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0be4ee10e4f343b36b16e5406c9f6d23d16d816d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626780"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
Belirtilen adreste geçerli olan sembole sahip olan çocuklarına sahip olur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findChildrenExByAddr ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `symtag`

[in] SymTagEnum Numaralamada tanımlandığı gibi, alınabilecek [altların sembol etiketlerini belirtir.](../../debugger/debug-interface-access/symtagenum.md) Tüm `SymTagNull` çocukların alınsı için olarak ayarlayın.

 `name`

[in] Alın eklenecek altların adını belirtir. Tüm `NULL` çocukların alınsı için olarak ayarlayın.

 `compareFlags`

[in] Ad eşleştirmeye uygulanacak karşılaştırma seçeneklerini belirtir. [NameSearchOptions Enumeration enumeration](../../debugger/debug-interface-access/namesearchoptions.md) değerleri tek başına veya birlikte kullanılabilir.

 `address`

[in] Sembolün adresi.

 `ppResult`

[out] Alınan [alt simgelerin listesini içeren bir IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Sembolün en az bir alt adı bulunursa veya alt alt bilgi bulunamasa döndürür; aksi takdirde `S_OK` bir hata kodu `S_FALSE` döndürür.

## <a name="remarks"></a>Açıklamalar
 Döndürülen yerel semboller canlı aralık bilgilerini içerir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)
