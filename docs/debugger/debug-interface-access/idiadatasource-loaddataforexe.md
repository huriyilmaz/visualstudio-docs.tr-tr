---
description: /.exedosyasıyla ilişkili hata ayıklama .dll hazırlar.
title: IDiaDataSource::loadDataForExe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 63158ea74b23dbd89995a3ee7608fad68e2a69d482aba9a76a7fd89d5d932b75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345279"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
/.exedosyasıyla ilişkili hata ayıklama .dll hazırlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT loadDataForExe (
   LPCOLESTR executable,
   LPCOLESTR searchPath,
   IUnknown* pCallback
);
```

#### <a name="parameters"></a>Parametreler
Yürütüle -bilir

[in] .exe veya .dll yolu.

Searchpath

[in] Hata ayıklama verilerini aramak için alternatif yol.

pCallback

[in] `IUnknown` [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)ve/veya [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) arabirimleri gibi hata ayıklama geri çağırma arabirimini destekleyen bir nesne arabirimi.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Aşağıdaki tabloda, bu yöntem için bazı olası hata kodları gösterir.

|Değer|Açıklama|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Dosya açılamadı veya dosyanın biçimi geçersiz.|
|E_PDB_FORMAT|Eski bir biçime sahip bir dosyaya erişmeye çalışıldı.|
|E_PDB_INVALID_SIG|İmza eşle değil.|
|E_PDB_INVALID_AGE|Yaş eşle değil.|
|E_ınvalıdarg|Geçersiz parametre.|
|E_unexpected|Veri kaynağı zaten hazırlanmıştır.|

## <a name="remarks"></a>Açıklamalar
.exe/.dll dosyasının hata ayıklama üst bilgisi, ilişkili hata ayıklama veri konumunu belirtir.

Bir sembol sunucusundan hata ayıklama verileri yüklüyse *symsrv.dll* kullanıcının uygulamasının veyamsdia140.dll'nin yüklü  olduğu dizinde veya sistem dizininde mevcut olması gerekir.

Bu yöntem, hata ayıklama üst bilgilerini okur ve ardından hata ayıklama verilerini arar ve hazırlar. Aramanın ilerleme durumu, isteğe bağlı olarak geri çağırmalar aracılığıyla rapor edilebilir ve denetlen olabilir. Örneğin, [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) yöntemi bir hata ayıklama dizini bulduğunda `IDiaDataSource::loadDataForExe` ve işleyene çağrılır.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) ve [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) arabirimleri, istemci uygulamanın yürütülebilir dosyadan verileri okumak için alternatif yöntemler sağlamasına olanak sağlar. Bu yöntemlere standart dosyanın I/O üzerinden doğrudan erişilemez.

Doğrulama olmadan bir .pdb dosyası yüklemek için [IDiaDataSource::loadDataFromPdb yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) kullanın.

.pdb dosyasını belirli ölçütlere göre doğrulamak için [IDiaDataSource::loadAndValidateDataFromPdb yöntemini](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) kullanın.

.pdb dosyasını doğrudan bellekten yüklemek için [IDiaDataSource::loadDataFromIStream yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) kullanın.

## <a name="example"></a>Örnek

```C++
class MyCallBack: public IDiaLoadCallback
{
...
};
MyCallBack callback;
...
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);
if (FAILED(hr))
{
    // Report error
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
