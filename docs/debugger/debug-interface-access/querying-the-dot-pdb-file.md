---
description: Program veritabanı dosyası (uzantı .pdb), projeyi derleme ve bağlama sırasında toplanan tür ve sembolik hata ayıklama bilgilerini içeren bir ikili dosyadır.
title: sorgusunu. Pdb Dosya | Microsoft Docs
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
ms.openlocfilehash: 02002589c309bcf4a639af27609e58d9688cb153c564b679b188e0535dd7d720
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379689"
---
# <a name="querying-the-pdb-file"></a>.Pdb Dosyasını Sorgulama
Program veritabanı dosyası (uzantı .pdb), projeyi derleme ve bağlama sırasında toplanan tür ve sembolik hata ayıklama bilgilerini içeren bir ikili dosyadır. /ZI veya **/Zi** ile bir C/C++ programı derleseniz veya  [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] **/debug** seçeneğiyle bir , veya programı derleseniz bir PDB dosyası oluşturulur. Nesne dosyaları, hata ayıklama bilgileri için .pdb dosyasına başvurular içerir. pdb dosyaları hakkında daha fazla bilgi için bkz. [PDB Dosyaları.](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)) Dia uygulaması, yürütülebilir bir görüntüdeki çeşitli semboller, nesneler ve veri öğeleri hakkında ayrıntıları almak için aşağıdaki genel adımları kullanabilir.

### <a name="to-query-the-pdb-file"></a>.pdb dosyasını sorgulamak için

1. [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) arabirimi oluşturarak bir veri kaynağı alın.

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

2. Hata [ayıklama bilgilerini yüklemek için IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) veya [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) çağrısında bulunur.

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

3. Hata [ayıklama bilgilerine erişim kazanmak için IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) çağrısıyla bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) açın.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Veri kaynağında sembolleri `IDiaSession` sorgulamak için içinde yöntemlerini kullanın.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Arabirimleri `IDiaEnum*` kullanarak hata ayıklama bilgilerini veya sembolleri veya diğer öğeleri numaralar ve taramalar.

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
