---
title: IDiaLineNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber interface
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 819fe28b9ba3fb95e749f0be53702dd7fdccf008
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743102"
---
# <a name="idialinenumber"></a>IDiaLineNumber
Bir bayt bloğundan bir kaynak dosya satır numarasıyla eşleme işlemini açıklayan bilgilere erişir.

## <a name="syntax"></a>Sözdizimi

```
IDiaLineNumber : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda `IDiaLineNumber` yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaLineNumber::get_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Görüntü metninin baytlarına katkıda bulunan compiland sembolü için bir başvuru alır.|
|[IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|Kaynak dosya nesnesine bir başvuru alır.|
|[IDiaLineNumber::get_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|Kaynak dosyadaki satır numarasını alır.|
|[IDiaLineNumber::get_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Deyim veya ifadenin bittiği tek tabanlı kaynak satır numarasını alır.|
|[IDiaLineNumber::get_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|İfadenin veya deyimin başladığı sütun numarasını alır.|
|[IDiaLineNumber::get_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|İfadenin veya deyimin bittiği sütun numarasını alır.|
|[IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Bir bloğun başladığı bellek adresinin bölüm kısmını alır.|
|[IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Bir bloğun başladığı bellek adresinin konum kısmını alır.|
|[IDiaLineNumber::get_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Bir bloğun görüntü göreli sanal adresini (RVA) alır.|
|[IDiaLineNumber::get_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Bir bloğun sanal adresini (VA) alır.|
|[IDiaLineNumber::get_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|Bir bloktaki bayt sayısını alır.|
|[IDiaLineNumber::get_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Bu satıra katkıda bulunan kaynak dosya için benzersiz bir kaynak dosya tanımlayıcısı alır.|
|[IDiaLineNumber::get_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|Bu satır bilgisinin program kaynağındaki bir deyimin başlangıcını açıkladığını belirten bir bayrak alır.|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Bu satıra katkıda bulunan compiland için benzersiz tanımlayıcıyı alır.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
[IDiaEnumLineNumbers:: Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) veya [IDiaEnumLineNumbers:: Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) yöntemlerini çağırarak bu arabirimi elde edin.

## <a name="example"></a>Örnek
Aşağıdaki işlev bir işlevde kullanılan satır numaralarını görüntüler (`pSymbol` tarafından temsil edilir).

```C++
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )
{
    ULONGLONG length = 0;
    DWORD     isect  = 0;
    DWORD     offset = 0;

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
                                      &pLines)
                      )
           )
        {
            CComPtr< IDiaLineNumber > pLine;
            DWORD celt      = 0;
            bool  firstLine = true;

            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&
                    celt == 1 )
            {
                DWORD offset;
                DWORD seg;
                DWORD linenum;
                CComPtr< IDiaSymbol >     pComp;
                CComPtr< IDiaSourceFile > pSrc;

                pLine->get_compiland( &pComp );
                pLine->get_sourceFile( &pSrc );
                pLine->get_addressSection( &seg );
                pLine->get_addressOffset( &offset );
                pLine->get_lineNumber( &linenum );
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );
                pLine = NULL;
                if ( firstLine )
                {
                    // sanity check
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;
                    if ( SUCCEEDED( pSession->findLinesByLinenum(
                                                  pComp,
                                                  pSrc,
                                                  linenum,
                                                  0,
                                                  &pLinesByLineNum)
                                  )
                       )
                    {
                        CComPtr< IDiaLineNumber > pLine;
                        DWORD celt;
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&
                                celt == 1 )
                        {
                            DWORD offset;
                            DWORD seg;
                            DWORD linenum;

                            pLine->get_addressSection( &seg );
                            pLine->get_addressOffset( &offset );
                            pLine->get_lineNumber( &linenum );
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );
                            pLine = NULL;
                        }
                    }
                    firstLine = false;
                }
            }
        }
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)
- [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)
