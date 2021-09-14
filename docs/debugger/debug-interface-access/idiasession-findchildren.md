---
description: Belirtilen bir üst tanımlayıcının adı ve sembol türüyle eşleşen tüm alt öğelerini alır.
title: 'IDiaSession:: findChildren | Microsoft Docs'
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629271"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Belirtilen bir üst tanımlayıcının adı ve sembol türüyle eşleşen tüm alt öğelerini alır.

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

'ndaki Üst öğeyi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. Bu üst simge bir işlev, modül veya blok ise, sözcük alt öğeleri içinde döndürülür `ppResult` . Üst simge bir tür ise, sınıf alt öğeleri döndürülür. Bu parametre ise, `NULL` `symtag` `SymTagExe` `SymTagNull` Genel kapsamı (.exe dosyası) döndüren veya olarak ayarlanması gerekir.

 `symtag`

'ndaki Alınacak alt öğelerin sembol etiketini belirtir. Değerler [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) numaralandırmasından alınır. `SymTagNull`Tüm alt öğeleri almak için olarak ayarlayın.

 `name`

'ndaki Alınacak alt öğelerin adını belirtir. `NULL`Tüm alt öğelerin alınması için olarak ayarlayın.

 `compareFlags`

'ndaki Ad eşleştirme için uygulanan karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.

 `ppResult`

dışı Alınan alt simgelerin listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, adıyla eşleşen işlev yerel değişkenlerinin nasıl bulunacağını gösterir `pFunc` `szVarName` .

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
