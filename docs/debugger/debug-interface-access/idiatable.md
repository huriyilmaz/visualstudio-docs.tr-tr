---
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7a573eb92d7c51079b0a7e97067abd155ae4fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738705"
---
# <a name="idiatable"></a>IDiaTable
Bir DIA veri kaynağı tablosunu numaralandırır.

## <a name="syntax"></a>Sözdizimi

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda `IDiaTable`yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Bu Numaralandırıcının [IEnumVARIANT arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) sürümünü alır.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Tablonun adını alır.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Tablodaki öğelerin sayısını alır.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Belirli bir giriş dizinine bir başvuru alır.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, Microsoft. VisualStudio. OLE. Interop ad alanındaki `IEnumUnknown` numaralandırma yöntemlerini uygular. `IEnumUnknown` numaralandırma arabirimi, [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) ve [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) metotlarından daha fazla tablo içeriğine yineleme yapmak için çok daha etkilidir.

`IDiaTable::Item` yönteminden veya `Next` yönteminden (Microsoft. VisualStudio. OLE. Interop ad alanında) döndürülen `IUnknown` arabiriminin yorumu, tablo türüne bağlıdır. Örneğin, `IDiaTable` arabirimi eklenen kaynakların listesini temsil ediyorsa, [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) arabirimi için `IUnknown` arabirimi sorgulanmalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
[IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) veya [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) yöntemlerini çağırarak bu arabirimi elde edin.

Aşağıdaki arabirimler `IDiaTable` arabirimiyle uygulanır (diğer bir deyişle, aşağıdaki arabirimlerden biri için `IDiaTable` arabirimini sorgulayabilirsiniz):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Örnek
İlk işlev `ShowTableNames`, oturumdaki tüm tabloların adlarını görüntüler. İkinci işlev `GetTable`, belirtilen arabirimi uygulayan bir tablonun tüm tablolarını arar. `UseTable`üçüncü işlevi, `GetTable` işlevinin nasıl kullanılacağını gösterir.

> [!NOTE]
> `CDiaBSTR`, bir `BSTR` sarmalayan ve örnekleme kapsam dışına geçtiğinde dizeyi serbest bırakma işleminde otomatik olarak işleyen bir sınıftır.

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
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
