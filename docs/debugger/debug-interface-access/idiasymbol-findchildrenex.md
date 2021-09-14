---
description: Sembolün children'larını alın. Program iyileştirme ile derlenmişse, döndürülen yerel semboller canlı aralık bilgilerini içerir.
title: IDiaSymbol::findChildrenEx | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626781"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Sembolün children'larını alın. Program iyileştirme ile derlenmişse, döndürülen yerel semboller canlı aralık bilgilerini içerir.

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

[in] SymTagEnum Numaralamada tanımlandığı gibi, alınabilecek [altların sembol etiketlerini belirtir.](../../debugger/debug-interface-access/symtagenum.md) Tüm `SymTagNull` çocukların alınsı için olarak ayarlayın.

 `name`

[in] Alın eklenecek altların adını belirtir. Tüm `NULL` çocukların alınsı için olarak ayarlayın.

 `compareFlags`

[in] Ad eşleştirmeye uygulanacak karşılaştırma seçeneklerini belirtir. [NameSearchOptions Enumeration enumeration](../../debugger/debug-interface-access/namesearchoptions.md) değerleri tek başına veya birlikte kullanılabilir.

 `ppResult`

[out] Alınan [alt simgelerin listesini içeren bir IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Sembolün en az bir alt adı bulunursa veya alt alt bilgi bulunamasa döndürür; aksi takdirde `S_OK` bir hata kodu `S_FALSE` döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem [IDiaSymbol::findChildren'ın genişletilmiş sürümüdür.](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

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
