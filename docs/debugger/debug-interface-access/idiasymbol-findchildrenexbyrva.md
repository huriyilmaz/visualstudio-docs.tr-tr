---
description: Belirtilen bir göreli sanal adreste (RVA) geçerli olan sembolün çocuklarını alır.
title: IDiaSymbol::findChildrenExByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c51a5ded5af919bd38cf5e83c2e86dd78246da31
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626763"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
Belirtilen bir göreli sanal adreste (RVA) geçerli olan sembolün çocuklarını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findChildrenExByRVA ( 
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

[in] RVA'yı belirtir.

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
