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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 97a1491b524311f8e48a1e59123e2648efa8d6c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058898"
---
# <a name="idiasession"></a>IDiaSession
Hata ayıklama sembolleri için bir sorgu bağlamı sağlar.

## <a name="syntax"></a>Syntax

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaSession` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Bu sembol deposuna karşılık gelen yürütülebilir dosyanın yükleme adresini alın. Bu, yöntemine geçirilen `put_loadAddress` değerle aynıdır.|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Bu sembol deposuna karşılık gelen yürütülebilir dosyanın yük adresini ayarlar. **Not:**  Bir nesnesi alasanız ve nesnesini kullanmaya `IDiaSession` başlamadan önce bu yöntemi çağırmanız önemlidir.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Genel kapsam için bir başvuru verir.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Sembol deposu içinde yer alan tüm tablolar için bir numaralayıcıyı alın.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Statik konumlarda tüm adlandırılmış semboller için bir numaralayıcıyı alın.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Ad ve sembol türüyle eşan belirtilen üst tanımlayıcının tüm altlarını verir.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Belirtilen bir adresi içeren veya en yakın olan belirtilen sembol türünü alın.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Belirtilen bir göreli sanal adresi (RVA) içeren veya en yakın olan simge türünü alır.|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Belirtilen sanal adresi (VA) içeren veya en yakın olan simge türünü alır.|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Belirtilen meta veri belirteci içeren sembolü alır.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|İki sembolün eşdeğer olup olduğunu denetler.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Benzersiz tanımlayıcısıyla bir sembolünü verir.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Belirtilen göreli sanal adresi ve uzaklığı içeren veya buna en yakın olan belirtilen sembol türünü alın.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Belirtilen sanal adresi ve uzaklığı içeren veya en yakın olan belirtilen sembol türünü alın.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Bir kaynak dosyayı compiland ve name ile alınır.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Kaynak dosya tanımlayıcısına göre bir kaynak dosyası verir.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Belirtilen bir derleme ve kaynak dosya tanımlayıcısı içindeki satır numaralarını verir.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Belirtilen bir adres içeren belirtilen bir derleme içinde satırları alınır.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Belirtilen bir göreli sanal adresi içeren belirtilen bir derlemede satırları alın.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Belirtilen adres aralığındaki satırlar için satır numarası bilgilerini bulur.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Belirtilen bir derlemede yer alan satırları kaynak dosyaya ve satır numarasına göre alın.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Öznitelik sağlayıcıları veya derleme işleminin diğer bileşenleri tarafından sembol deposuna yerleştirilmiş bir kaynağı alın.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Hata ayıklama veri akışlarının numaralandı bir dizisini alın.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|bir istemcinin belirli bir adresteki tüm satır içi çerçeveler üzerinde devamsını sağlayan bir sabit adı verir.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Bir istemcinin belirtilen bir göreli sanal adresteki (RVA) tüm satır içi çerçeveler üzerinde devamsını sağlayan bir sabit değer alır.|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçeveler üzerinde devamını sağlayan bir sabit değer alır.|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Bir istemcinin, belirtilen üst simgeyle satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırır.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Bir istemcinin, belirtilen üst simge tarafından satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında ve belirtilen adres aralığında yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırır.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Bir istemcinin, belirtilen üst simge tarafından satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında ve belirtilen göreli sanal adres (RVA) içinde yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak alır.|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Bir istemcinin, belirtilen üst simge tarafından satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında ve belirtilen sanal adres (VA) içinde yer alan tüm işlevlerin satır numarası bilgileri arasında bir numaralama alır.|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Bir istemcinin, belirtilen kaynak dosya ve satır numarasında satır içine alınan, doğrudan veya dolaylı olarak tüm işlevlerin satır numarası bilgileri arasında bir numaralandırarak bir numaralandırır.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Bir istemcinin belirtilen bir adla eş değere sahip tüm satırlı işlevlerin satır numarası bilgileri arasında bir süre boyunca devam edatsını sağlayan bir numaralama verir.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Belirtilen etiket değerinin üst Hızlandırıcı saplama işlevinde karşılık gelen değişkeni için simgelerin bir sabit değerini döndürür.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Karşılık gelen bir etiket değeri verilmelidir, bu yöntem belirtilen bir göreli sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde yer alan sembollerin bir numaralama döndürür.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Belirtilen satır içi işlev adına karşılık gelen satır içi çerçeveler için simgelerin bir sabit adını döndürür.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Belirtilen kaynak konuma karşılık gelen satır içi çerçeveler için simgelerin bir sabit bir sabitlevasyonu döndürür.|

## <a name="remarks"></a>Açıklamalar
Nesneyi oluşturduktan sonra [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) yönteminin çağrıl olması ve sembollerin tüm sanal adres `IDiaSession` (VA) özelliklerinin erişilebilir olması için yöntemine geçirilen değerin sıfır olmayan olması `put_loadAddress` gerekir. Yükleme adresi, hata ayıklaması yapılan yürütülebilir dosyayı yüklemiş olan programdan gelir. Örneğin, yürütülebilir dosya için bir tanıtıcı verilen yürütülebilir dosyanın yükleme adresini almak için Win32 `GetModuleInformation` işlevini çağırabilirsiniz.

## <a name="example"></a>Örnek
Bu örnekte, uygulamanın genel `IDiaSession` olarak başlatan bir parçası olarak arabirimin nasıl DIA SDK.

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
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

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
