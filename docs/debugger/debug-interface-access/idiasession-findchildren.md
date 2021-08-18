---
description: Ad ve sembol türüyle eşan belirtilen üst tanımlayıcının tüm altlarını verir.
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 13a1bcf4a4d5fed816ef467cdc15c5c6fb974f18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139150"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Ad ve sembol türüyle eşan belirtilen üst tanımlayıcının tüm altlarını verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

[in] Üst [nesneyi temsil eden bir IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. Bu üst simge bir işlev, modül veya blok ise sözcüksel alt öğesi içinde `ppResult` döndürülür. Üst simge bir türse, sınıf alt öğesi döndürülür. Bu parametre `NULL` ise, genel kapsamı döndüren veya olarak ayar `symtag` `SymTagExe` `SymTagNull` .exe.

 `symtag`

[in] Alın eklenecek alt kümenin sembol etiketini belirtir. Değerler [SymTagEnum Numaralama numaralarından](../../debugger/debug-interface-access/symtagenum.md) alınır. Tüm `SymTagNull` children'ları almak için olarak ayarlayın.

 `name`

[in] Alın eklenecek altların adını belirtir. Tüm `NULL` çocukların alınsı için olarak ayarlayın.

 `compareFlags`

[in] Ad eşleştirmeye uygulanan karşılaştırma seçeneklerini belirtir. [NameSearchOptions Enumeration enumeration](../../debugger/debug-interface-access/namesearchoptions.md) değerleri tek başına veya birlikte kullanılabilir.

 `ppResult`

[out] Alınan [alt sembollerin listesini içeren bir IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, adıyla eşleyen işlevin yerel `pFunc` değişkenlerini bulma adımlarını `szVarName` gösterir.

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>Ayrıca bkz.
- [Genel Bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
