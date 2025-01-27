---
description: Veri kaynağında bulunan çeşitli satır numaralarını numaralar.
title: IDiaEnumLineNumbers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers interface
ms.assetid: cdf07b4f-19e4-4dcd-8af8-c2dbca586a7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 64fea0497f1cc8d8767a71eb4e06d77ae4b56e58
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630213"
---
# <a name="idiaenumlinenumbers"></a>IDiaEnumLineNumbers
Veri kaynağında bulunan çeşitli satır numaralarını numaralar.

## <a name="syntax"></a>Syntax

```
IDiaEnumLineNumbers : IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaEnumLineNumbers` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaEnumLineNumbers::get__NewEnum](../../debugger/debug-interface-access/idiaenumlinenumbers-get-newenum.md)|Bu [numaralayıcının IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) Arabirimi sürümünü alın.|
|[IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)|Satır numaralarının sayısını verir.|
|[IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)|Bir dizin ile bir satır numarası alınır.|
|[IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)|Numaralama dizisinde belirtilen sayıda satır numarası verir.|
|[IDiaEnumLineNumbers::Skip](../../debugger/debug-interface-access/idiaenumlinenumbers-skip.md)|Bir numaralama dizisinde belirtilen sayıda satır numarasını atlar.|
|[IDiaEnumLineNumbers::Reset](../../debugger/debug-interface-access/idiaenumlinenumbers-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[IDiaEnumLineNumbers::Clone](../../debugger/debug-interface-access/idiaenumlinenumbers-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, [IDiaSession](../../debugger/debug-interface-access/idiasession.md) arabiriminde aşağıdaki yöntemlerden biri çağrılarak elde edilir:

- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)

- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)

- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)

- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)

- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)

## <a name="example"></a>Örnek
Bu örnekte, arabirimin bir `IDiaEnumLineNumbers` oturumdan nasıl alınarak elde edilir? Bu örnekte, bir işlevin satır numarası numaralama işlevinin (ile temsil edilen) nasıl elde etmek olduğu `pSymbol` gösterir. Satır numaralarını kullanmanın daha eksiksiz bir örneği için bkz. [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) arabirimi.

```C++
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )
{
    ULONGLONG length = 0;
    DWORD isect = 0;
    DWORD offset = 0;
    pSymbol->get_addressSection( &isect );
    pSymbol->get_addressOffset( &offset );
    pSymbol->get_length( &length );
    if ( isect != 0 && length > 0 )
    {
        CComPtr< IDiaEnumLineNumbers > pLines;
        if ( SUCCEEDED( pSession->findLinesByAddr(
                                      isect,
                                      offset,
                                      static_cast<DWORD>( length ),
                                      &pLines )
                      )
           )
        {
            // Do something with the enumeration
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
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
