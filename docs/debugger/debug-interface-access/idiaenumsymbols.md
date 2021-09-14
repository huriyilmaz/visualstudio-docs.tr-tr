---
description: Veri kaynağında bulunan çeşitli sembolleri numaralar.
title: IDiaEnumSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6f8578ca439d32dbaae13356b0f76fb890d2d5ff
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629997"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
Veri kaynağında bulunan çeşitli sembolleri numaralar.

## <a name="syntax"></a>Syntax

```
IDiaEnumSymbols : IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaEnumSymbols` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Bu `IEnumVARIANT Interface` numaralayıcının sürümünü alınır.|
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Sembol sayısını alın.|
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Bir dizini kullanarak sembolünü alan.|
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Numaralama dizisinde belirtilen sayıda simgeyi alan.|
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Bir numaralama dizisinde belirtilen sayıda simgeyi atlar.|
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, belirli bir sembol türüne göre (kullanıcı tanımlı türler) veya `SymTagUDT` gibi gruplara sahip semboller `SymTagBaseClass` sağlar. Adrese göre gruplu sembollerle çalışmak için [IDiaEnumSymbolsByAddr arabirimini](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) kullanın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Aşağıdaki yöntemleri çağırarak bu arabirimi alın:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)

## <a name="example"></a>Örnek
Bu örnekte, kullanıcı tanımlı türleri (UDT' ler) listeleye bu numaralamanın nasıl alınarak arabirimin nasıl alınacak ve sonra `IDiaEnumSymbols` bu numaralamanın nasıl kullanacağız?

> [!NOTE]
> `CDiaBSTR` , bir sarmalama ve örnekleme kapsam dışında olduğunda dize serbest bırakarak otomatik `BSTR` olarak tanıtıcı bir sınıftır.

```C++
void ShowUDTs(IDiaSymbol *pGlobals)
{
    CComPtr<IDiaEnumSymbols> pEnum;
    CComPtr<IDiaSymbol> pSymbol;
    HRESULT hr;

    hr = pGlobals->findChildren(SymTagUDT,
                                NULL,
                                nsfCaseInsensitive | nsfUndecoratedName,
                                &pEnum);
    if (hr == S_OK)
    {
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR name;
            if ( pSymbol->get_name( &name ) != S_OK )
                Fatal( "get_name" );
            printf( "Found UDT: %ws\n", name );
            pSymbol = 0;
        }
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
