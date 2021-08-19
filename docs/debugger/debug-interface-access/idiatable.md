---
description: DIA veri kaynağı tablolarını numaralar.
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7f8dc87343a425d87c2936b6667f350c456b45cf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113214"
---
# <a name="idiatable"></a>IDiaTable
DIA veri kaynağı tablolarını numaralar.

## <a name="syntax"></a>Syntax

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaTable` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Bu [numaralayıcının IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) Arabirimi sürümünü alın.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Tablonun adını alır.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Tablodaki öğe sayısını alır.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Belirli bir giriş dizinine başvuru verir.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, `IEnumUnknown` Microsoft.VisualStudio.OLE.Interop ad alanında numaralama yöntemlerini kullanır. Enumeration arabirimi, tablo içeriği üzerinde `IEnumUnknown` [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) ve [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md) yöntemlerine göre daha verimlidir.

yönteminden veya yönteminden döndürülen arabirimin `IUnknown` `IDiaTable::Item` yorumu `Next` (Microsoft.VisualStudio.OLE.Interop ad alanında) tablonun türüne bağlıdır. Örneğin, arabirim, `IDiaTable` bir eklenir kaynaklar listesini temsil ediyorsa, arabirim `IUnknown` [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) arabirimi için sorgu gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) veya [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) yöntemlerini çağırarak bu arabirimi alın.

Aşağıdaki arabirimler arabirimiyle `IDiaTable` uygulanır (yani, arabirimi aşağıdaki `IDiaTable` arabirimlerden birini sorgular):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Örnek
İlk işlev olan `ShowTableNames` , oturumdaki tüm tabloların adlarını görüntüler. İkinci işlev olan `GetTable` , belirtilen arabirimi uygulayan bir tablo için tüm tabloları arar. Üçüncü işlev olan `UseTable` , işlevinin nasıl kullanılı olduğunu `GetTable` gösterir.

> [!NOTE]
> `CDiaBSTR` , bir sarmalama ve örnekleme kapsam dışında olduğunda dize serbest serbest bırakarak otomatik `BSTR` olarak tanıtıcı bir sınıftır.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
