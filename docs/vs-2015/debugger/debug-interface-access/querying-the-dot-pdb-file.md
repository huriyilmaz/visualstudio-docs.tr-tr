---
title: Sorgulanıyor. Pdb dosyası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b9013d41ac4d5ca890e7cc9e09b5eb9415cb640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691324"
---
# <a name="querying-the-pdb-file"></a>.Pdb Dosyasını Sorgulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Program veritabanı dosyası (uzantısı. pdb), projeyi derleyip bağlama sırasında toplanan tür ve simgesel hata ayıklama bilgilerini içeren bir ikili dosyadır. **/Zi** veya **/Zi** ya da [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] **/Debug** seçeneğiyle bir C/C++ programı derlerken bir PDB dosyası oluşturulur. Nesne dosyaları hata ayıklama bilgileri için. pdb dosyasına başvuruları içerir. Pdb dosyaları hakkında daha fazla bilgi için bkz. [pdb dosyaları](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f). Bir DIA uygulaması, yürütülebilir bir görüntü içindeki çeşitli semboller, nesneler ve veri öğeleri hakkında ayrıntıları almak için aşağıdaki genel adımları kullanabilir.  
  
### <a name="to-query-the-pdb-file"></a>. Pdb dosyasını sorgulamak için  
  
1. [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) arabirimi oluşturarak veri kaynağı alma.  
  
    ```cpp#  
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
  
    ```cpp#  
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
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. `IDiaSession`Veri kaynağındaki sembolleri sorgulamak için içindeki yöntemleri kullanın.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. `IDiaEnum*`Simgeleri veya hata ayıklama bilgilerinin diğer öğelerini numaralandırmak ve taramak için arabirimlerini kullanın.  
  
    ```cpp#  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
