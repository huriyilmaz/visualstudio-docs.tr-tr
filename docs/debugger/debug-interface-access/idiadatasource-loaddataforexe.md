---
description: .exe/.dll dosyasıyla ilişkili hata ayıklama verilerini açar ve hazırlar.
title: 'IDiaDataSource:: loadDataForExe | Microsoft Docs'
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
ms.openlocfilehash: 6e11a6d85e8a33803b7cbf8b912d3db834996753
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154698"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
.exe/.dll dosyasıyla ilişkili hata ayıklama verilerini açar ve hazırlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT loadDataForExe (
   LPCOLESTR executable,
   LPCOLESTR searchPath,
   IUnknown* pCallback
);
```

#### <a name="parameters"></a>Parametreler
yürütülür

'ndaki .exe veya .dll dosyasının yolu.

searchPath

'ndaki Hata ayıklama verilerini aramak için alternatif yol.

pCallback

'ndaki Bir `IUnknown` hata ayıklama geri [çağırması](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [ıdareadexeatoffsetcallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)ve/veya [ıdareadexeatrboş allback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) arabirimleri gibi bir hata ayıklama geri çağırma arabirimini destekleyen bir nesne için arabirim.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda, bu yöntem için olası hata kodlarının bazıları gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Dosya açılamadı veya dosya geçersiz bir biçime sahip.|
|E_PDB_FORMAT|Eski biçimdeki bir dosyaya erişme girişiminde bulunuldu.|
|E_PDB_INVALID_SIG|İmza eşleşmiyor.|
|E_PDB_INVALID_AGE|Yaş eşleşmiyor.|
|E_INVALIDARG|Geçersiz parametre.|
|E_UNEXPECTED|Veri kaynağı zaten hazırlandı.|

## <a name="remarks"></a>Açıklamalar
.exe/.dll dosyasının hata ayıklama üst bilgisi, ilişkili hata ayıklama veri konumunu adlandırır.

Bir sembol sunucusundan hata ayıklama verileri yüklüyorsanız, *symsrv.dll* kullanıcının uygulamasının veya *msdia140.dll* yüklendiği aynı dizinde bulunmalı veya sistem dizininde bulunması gerekir.

Bu yöntem hata ayıklama üstbilgisini okur ve hata ayıklama verilerini arar ve hazırlar. Aramanın ilerleme durumu isteğe bağlı olarak, geri çağrılar aracılığıyla raporlanabilmesi ve denetlenemeyebilir. Örneğin, yöntem bir hata ayıklama dizini bulduğunda ve işlediğinde, [ıaloadcallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) çağrılır `IDiaDataSource::loadDataForExe` .

[Iareaareadexeatoffsetcallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) ve [ıseareadexeatrboş allback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) arabirimleri, bir dosyaya doğrudan standart dosya g/ç aracılığıyla erişilebilmesi durumunda, istemci uygulamanın yürütülebilir dosyadan veri okumak için alternatif yöntemler sağlamasına izin verir.

Bir. pdb dosyasını doğrulama olmadan yüklemek için [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodunu kullanın.

. Pdb dosyasını belirli ölçütlere karşı doğrulamak için [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodunu kullanın.

Bir. pdb dosyasını doğrudan bellekten yüklemek için [IDiaDataSource:: Loaddatafromistreaı](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodunu kullanın.

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
