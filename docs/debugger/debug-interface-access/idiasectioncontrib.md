---
description: Bölüm katkısını açıklayan, yani bir derleme tarafından görüntüye katkıda bulunan bitişik bir bellek bloğu olan verileri alınır.
title: IDiaSectionContrib | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 639386da6ee310e37390264550d5f101df7390a4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081456"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
Bölüm katkısını açıklayan, yani bir derleme tarafından görüntüye katkıda bulunan bitişik bir bellek bloğu olan verileri alınır.

## <a name="syntax"></a>Syntax

```
IDiaSectionContrib : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaSectionContrib` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Bu bölüme katkıda bulunan compiland simgesine bir başvuru verir.|
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Katkı adresinin bölüm bölümünü alın.|
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Katkı adresinin uzaklık bölümünü alın.|
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Katkının görüntü göreli sanal adresini (RVA) alın.|
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Katkının sanal adresini (VA) alın.|
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Bir bölümdeki bayt sayısını alan.|
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Bölümün belleğinin yetersiz olup olmadığını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Bölümün bir sonraki bellek sınırına alınıp alınmay olmadığını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|bölümünün yürütülebilir kod içerdiğini belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Bölümünün 16 bit kod içerdiğini belirten bir bayrağını alın.|
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|bölümünün başlatılan veriler içerdiğini belirten bir bayrağını alın.|
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Bölümünün, uninitialized data (uninitialized data) içerdiğini belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Bir bölümün açıklamalar mı yoksa benzer bilgiler mi içerdiğini belirten bayrağını alın.|
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Bellek içinde görüntünün bir parçası olmadan önce bölümün kaldırılmış olup olmadığını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Bölümünün bir COMDAT kaydı olup olmadığını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Bölümü atıp atılamayacaklarını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Bölümün önbelleğe alınıp alınamay olmadığını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Bölümün bellekte paylaşılap paylaşılmay olmadığını belirten bir bayrağını alın.|
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Bölümün kod olarak yürütülebilir olup olmadığını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Bölümün okunıp okuna olmadığını belirten bir bayrak alınır.|
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Bölümün yazıp yazılanamayrı belirten bir bayrağını alın.|
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|bölümündeki verilerin döngüsel yedeklilik denetimi (CRC) alınır.|
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Bölümü için yeniden konumlandırma bilgisinin CRC'sine ulaşabilirsiniz.|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|bölümünün compiland tanımlayıcısını alın.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) ve [IDiaEnumSectionContribs::Next yöntemleri çağrılarak](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) elde edilir. Arabirimi alma [örneği için bkz. IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) `IDiaSectionContrib` arabirimi.

## <a name="example"></a>Örnek
Bu işlev, ilişkili sembollerle birlikte her bölümün adresini gösterir. Arabirimin [nasıl elde olduğunu görmek için bkz. IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) `IDiaSectionContrib` arabirimi.

```C++
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)
{
    if (pSecContrib != NULL && pSession != NULL)
    {
        DWORD rva;
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )
        {
            printf( "\taddr: 0x%.8X", rva );
            pSecContrib = NULL;
            CComPtr<IDiaSymbol> pSym;
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
            {
                CDiaBSTR name;
                DWORD    tag;
                pSym->get_symTag( &tag );
                pSym->get_name( &name );
                printf( "     symbol: %ws (%ws)\n",
                        name != NULL ? name : L"",
                        szTags[ tag ] );
            }
            else
            {
                printf( "<no symbol found?>\n" );
            }
        }
        else
        {
            DWORD isect;
            DWORD offset;
            pSecContrib->get_addressSection( &isect );
            pSecContrib->get_addressOffset( &offset );
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );
            pSecContrib = NULL;
            CComPtr<IDiaSymbol> pSym;
            if ( SUCCEEDED( psession->findSymbolByAddr(
                                              isect,
                                              offset,
                                              SymTagNull,
                                              &pSym )
                          )
               )
            {
                CDiaBSTR name;
                DWORD    tag;
                pSym->get_symTag( &tag );
                pSym->get_name( &name );
                printf( "     symbol: %ws (%ws)\n",
                    name != NULL ? name : L"",
                    szTags[ tag ] );
            }
            else
            {
                printf( "<no symbol found?>\n" );
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
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)
- [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)
