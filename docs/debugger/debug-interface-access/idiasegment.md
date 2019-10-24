---
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 855b40f3d35d884a366e8fdc36ed1ec4f2bef85a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742333"
---
# <a name="idiasegment"></a>IDiaSegment
Bölüm numarasından verileri adres alanının kesimlerine eşler.

## <a name="syntax"></a>Sözdizimi

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda `IDiaSegment` yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Segment numarasını alır.|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Bölümün başladığı Dilimlerdeki sapmayı alır.|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Kesimdeki bayt sayısını alır.|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Segmentin okunup okunamayacağını gösteren bir bayrak alır.|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Segmentin değiştirilip değiştirilemeyeceğini belirten bir bayrak alır.|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Segmentin yürütülebilir olup olmadığını gösteren bir bayrak alır.|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Bu segmentle eşleşen bölüm numarasını alır.|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Bölümün başlangıcının göreli sanal adresini (RVA) alır.|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Bölümün başlangıcının sanal adresini (VA) alır.|

## <a name="remarks"></a>Açıklamalar
DIA SDK, göreli sanal adreslere göre Bölüm uzaklığına zaten Çeviriler gerçekleştirdiğinden, çoğu uygulama segment eşlemesindeki bilgilerden bu bilgileri kullanmaz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
[IDiaEnumSegments:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) veya [IDiaEnumSegments:: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) yöntemlerini çağırarak bu arabirimi elde edin. Ayrıntılar için örneğe bakın.

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
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)
- [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
