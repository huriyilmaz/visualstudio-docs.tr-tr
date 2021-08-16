---
description: Haritalar numarasından adres alanı segmentlerine veri içerir.
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: eaa77f3779fa6bcf8708d53437e0194ec6c14a026abe57b11ca98a75e2f3d6b8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391947"
---
# <a name="idiasegment"></a>IDiaSegment
Haritalar numarasından adres alanı segmentlerine veri içerir.

## <a name="syntax"></a>Syntax

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaSegment` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Segment numarasını alın.|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Bölümün başladığı segmentlerde uzaklığı alınır.|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Segmentte bayt sayısını alan.|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Segmentin okunıp okuna olmadığını belirten bir bayrak alma.|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Segmentin değiştirilip değiştirileile olmadığını belirten bir bayrak alınır.|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Kesimin yürütülebilir olup olmadığını belirten bir bayrak alınır.|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Bu segmentle eşilen bölüm numarasını alın.|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Bölümün başlangıcının göreli sanal adresini (RVA) alan.|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Bölümün başlangıcının sanal adresini (VA) alın.|

## <a name="remarks"></a>Açıklamalar
Kaynak DIA SDK bölüm uzaklığından göreli sanal adreslere çeviriler yaptığı için, çoğu uygulama segment haritasında bilgileri kullanmaz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) veya [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) yöntemlerini çağırarak bu arabirimi alın. Ayrıntılar için örneğine bakın.

## <a name="example"></a>Örnek
Bu işlev, bir tablodaki tüm segmentlerin adresini ve en yakın simgeyi görüntüler.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSegments ),
                               (void**)&pSegments )
                  )
       )
    {
        CComPtr<IDiaSegment> pSegment;
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&
                celt == 1 )
        {
            DWORD rva;
            DWORD seg;

            pSegment->get_addressSection( &seg );
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )
            {
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );
                pSegment = NULL;

                CComPtr<IDiaSymbol> pSym;
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
                {
                    CDiaBSTR name;
                    DWORD    tag;

                    pSym->get_symTag( &tag );
                    pSym->get_name( &name );
                    printf( "\tClosest symbol: %ws (%ws)\n",
                            name != NULL ? name : L"",
                            szTags[ tag ] );
                }
            }
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
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)
- [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
