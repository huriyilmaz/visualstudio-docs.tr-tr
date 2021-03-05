---
description: Hata ayıklama sembolleri için bir sorgu bağlamı sağlar.
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fc8e3b69321e89959ea2367488e4601269834d3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156967"
---
# <a name="idiasession"></a>IDiaSession
Hata ayıklama sembolleri için bir sorgu bağlamı sağlar.

## <a name="syntax"></a>Syntax

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaSession` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini alır. Bu, yöntemine geçirilen değerdir `put_loadAddress` .|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini ayarlar. **Note:**  `IDiaSession` Nesne alırken ve nesnesini kullanmaya başlamadan önce bu yöntemi çağırmak önemlidir.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Genel kapsama bir başvuru alır.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Sembol deposunda bulunan tüm tablolar için bir Numaralandırıcı alır.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Statik konumlarda tüm adlandırılmış semboller için bir Numaralandırıcı alır.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Belirtilen bir üst tanımlayıcının adı ve sembol türüyle eşleşen tüm alt öğelerini alır.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Belirtilen bir adrese sahip veya en yakın olan, belirtilen bir sembol türünü alır.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Belirtilen bir göreli sanal adres (RVA) içeren veya en yakın olan, belirtilen bir sembol türünü alır.|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Belirtilen bir sanal adrese (VA) sahip veya en yakın olan, belirtilen bir sembol türünü alır.|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Belirtilen meta veri belirtecini içeren simgeyi alır.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|İki sembolün eşdeğer olup olmadığını denetler.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Bir sembolü benzersiz tanımlayıcısına göre alır.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Belirtilen bir göreli sanal adresi ve sapmayı içeren veya en yakın olan, belirtilen bir sembol türünü alır.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Belirtilen bir sanal adresi ve sapmayı içeren veya en yakın olan, belirtilen bir sembol türünü alır.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Compiland ve Name ile bir kaynak dosyası alır.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Kaynak dosya tanımlayıcısına göre bir kaynak dosyası alır.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Belirtilen bir compiland ve kaynak dosya tanımlayıcısı içindeki satır numaralarını alır.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Belirtilen bir adresi içeren belirtilen bir compiland içindeki satırları alır.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Belirtilen bir göreli sanal adresi içeren belirtilen bir compiland içindeki satırları alır.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Belirtilen adres aralığında yer alan satırlar için satır numarası bilgilerini bulur.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Kaynak dosya ve satır numarasına göre belirtilen bir compiland içindeki satırları alır.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Öznitelik sağlayıcıları veya derleme sürecinin diğer bileşenleri tarafından sembol deposuna yerleştirilmiş bir kaynağı alır.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Hata ayıklama veri akışlarının numaralandırılmış bir dizisini alır.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Bir istemcinin belirli bir adresteki tüm satır içi çerçeveler üzerinde yineleme yapmasına izin veren bir sabit listesi alır.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Bir istemcinin belirtilen göreli sanal adreste (RVA) bulunan tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Bir istemcinin, belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır içi tüm işlevlerin satır numarası bilgilerini yinelemesinden izin veren bir sabit listesi alır.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Bir istemcinin, belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgilerini, belirtilen üst simgeye göre veya belirtilen adres aralığında bulundurarak yinelemesinden izin veren bir sabit listesi alır.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Bir istemcinin, belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgileri üzerinden yineleyebilir ve belirtilen göreli sanal adres (RVA) içinde yer alır.|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Bir istemcinin, belirtilen ana sembolüyle doğrudan veya dolaylı olarak satır numarası bilgileri üzerinden yineleme yapmasına izin veren ve belirtilen sanal adres (VA) içinde yer alan bir sabit listesi alır.|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Bir istemcinin, belirtilen kaynak dosyasında ve satır numarasında satır içine alınmış, doğrudan veya dolaylı olarak satır numarası bilgilerini yinelemesinden izin veren bir sabit listesi alır.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Bir istemcinin, belirtilen bir adla eşleşen tüm satır numarası işlevlerinin satır numarası bilgilerini yinelemesinden izin veren bir sabit listesi alır.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Belirtilen etiket değerinin üst Hızlandırıcı saplama işlevinde karşılık geldiği değişken için bir sembol numaralandırması döndürür.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Karşılık gelen bir etiket değeri verildiğinde, bu yöntem belirtilen bir ilişkili sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde bulunan simgelerin bir listesini döndürür.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler için simgelerin bir listesini döndürür.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Belirtilen kaynak konumuna karşılık gelen satır içi çerçeveler için simgelerin bir listesini döndürür.|

## <a name="remarks"></a>Açıklamalar
Nesne oluşturulduktan sonra [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) yöntemini çağırmak önemlidir `IDiaSession` — ve simgelere geçirilen değer, `put_loadAddress` sembollerin herhangi BIR sanal adres (VA) özelliklerinin erişilebilir olması için sıfır dışında bir değer olmalıdır. Yükleme adresi, hata ayıklamakta olan yürütülebilir dosyayı yükleyen herhangi bir programdan gelir. Örneğin, yürütülebilir dosya için `GetModuleInformation` bir tanıtıcı verilen yükleme adresini almak üzere Win32 işlevini çağırabilirsiniz.

## <a name="example"></a>Örnek
Bu örnek, `IDiaSession` DIA SDK genel başlatmanın bir parçası olarak arabirimin nasıl alınacağını gösterir.

```C++
CComPtr<IDiaDataSource> pSource;
ComPtr<IDiaSession> psession;

void InitializeDIA(const char *szFilename)
{
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,
                                   NULL,
                                   CLSCTX_INPROC_SERVER,
                                   __uuidof( IDiaDataSource ),
                                  (void **) &pSource);
    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename,
              szFilename,
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [Genel Bakış](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [.Pdb Dosyasını Sorgulama](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
