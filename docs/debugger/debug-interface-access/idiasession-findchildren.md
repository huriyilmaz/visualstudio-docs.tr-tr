---
title: 'IDiaSession:: findChildren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca6778e5697c5f8821322c19d706d733d7f2b9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742297"
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

'ndaki Üst öğeyi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. Bu üst simge bir işlev, modül veya blok ise, sözcük alt öğeleri `ppResult` döndürülür. Üst simge bir tür ise, sınıf alt öğeleri döndürülür. Bu parametre `NULL`, `symtag` genel kapsamı (. exe dosyası) döndüren `SymTagExe` veya `SymTagNull` olarak ayarlanmalıdır.

 `symtag`

'ndaki Alınacak alt öğelerin sembol etiketini belirtir. Değerler [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) numaralandırmasından alınır. Tüm alt öğeleri almak için `SymTagNull` olarak ayarlayın.

 `name`

'ndaki Alınacak alt öğelerin adını belirtir. Tüm alt öğelerin alınabilmesi için `NULL` olarak ayarlayın.

 `compareFlags`

'ndaki Ad eşleştirme için uygulanan karşılaştırma seçeneklerini belirtir. [NameSearchOptions numaralandırma](../../debugger/debug-interface-access/namesearchoptions.md) numaralandırmasındaki değerler tek başına veya birlikte kullanılabilir.

 `ppResult`

dışı Alınan alt simgelerin listesini içeren bir [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, ad `szVarName` eşleşen işlev `pFunc` yerel değişkenlerinin nasıl bulunacağını gösterir.

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>Ayrıca bkz.
- [Genel bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions Numaralandırması](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)