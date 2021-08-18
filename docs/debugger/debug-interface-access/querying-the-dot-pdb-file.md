---
description: Program veritabanı dosyası (uzantısı. pdb), projeyi derleyip bağlama sırasında toplanan tür ve simgesel hata ayıklama bilgilerini içeren bir ikili dosyadır.
title: Sorgulanıyor. Pdb dosyası | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4da3527b8f6834a7fb36077e73ec193204803d80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097631"
---
# <a name="querying-the-pdb-file"></a>.Pdb Dosyasını Sorgulama
Program veritabanı dosyası (uzantısı. pdb), projeyi derleyip bağlama sırasında toplanan tür ve simgesel hata ayıklama bilgilerini içeren bir ikili dosyadır. **/Zi** veya **/Zi** ya da [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] **/Debug** seçeneğiyle bir C/C++ programı derlerken bir PDB dosyası oluşturulur. Nesne dosyaları hata ayıklama bilgileri için. pdb dosyasına başvuruları içerir. Pdb dosyaları hakkında daha fazla bilgi için bkz. [pdb dosyaları](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Bir DIA uygulaması, yürütülebilir bir görüntü içindeki çeşitli semboller, nesneler ve veri öğeleri hakkında ayrıntıları almak için aşağıdaki genel adımları kullanabilir.

### <a name="to-query-the-pdb-file"></a>. Pdb dosyasını sorgulamak için

1. [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) arabirimi oluşturarak veri kaynağı alma.

    ```C++
    CComPtr<IDiaDataSource> pSource;
    hr = CoCreateInstance( CLSID_DiaSource,
                           NULL,
                           CLSCTX_INPROC_SERVER,
                           __uuidof( IDiaDataSource ),
                          (void **) &pSource);

    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    ```

2. Hata ayıklama bilgilerini yüklemek için [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) veya [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) öğesini çağırın.

    ```C++
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    ```

3. Hata ayıklama bilgilerine erişim kazanmak için [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) öğesini çağırıp bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) açın.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. `IDiaSession`Veri kaynağındaki sembolleri sorgulamak için içindeki yöntemleri kullanın.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. `IDiaEnum*`Simgeleri veya hata ayıklama bilgilerinin diğer öğelerini numaralandırmak ve taramak için arabirimlerini kullanın.

    ```C++
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )
    {
        // Do something with each IDiaTable.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
