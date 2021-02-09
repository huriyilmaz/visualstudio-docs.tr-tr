---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bee496e8386185a3eb9393934b83da89286d0ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865225"
---
# <a name="idiadatasource"></a>IDiaDataSource
Hata ayıklama sembolleri kaynağına erişimi başlatır.

## <a name="syntax"></a>Syntax

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaDataSource` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Son yükleme hatası için dosya adını alır.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Bir program veritabanı (. pdb) dosyasını açıp hata ayıklama veri kaynağı olarak hazırlar.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Açılır ve program veritabanı (. pdb) dosyasının belirtilen imza bilgileriyle eşleştiğini doğrular; . pdb dosyasını bir hata ayıklama veri kaynağı olarak hazırlar.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|. Exe/. dll dosyasıyla ilişkili hata ayıklama verilerini açar ve hazırlar.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Bellek içi veri akışı aracılığıyla erişilen bir program veritabanı (. pdb) dosyasında depolanan hata ayıklama verilerini hazırlar.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Sembolleri sorgulamak için bir oturum açar.|

## <a name="remarks"></a>Açıklamalar
Arabirimin yükleme yöntemlerinden birine yapılan çağrı `IDiaDataSource` , sembol kaynağını açar. [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) yöntemine yapılan başarılı bir çağrı, veri kaynağını sorgulamayı destekleyen bir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) arabirimi döndürüyor. Load yöntemi dosyayla ilgili bir hata döndürürse, [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) yöntemi dönüş değeri hatayla ilişkili dosya adını içerir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, `CoCreateInstance` işlevi sınıf tanımlayıcısıyla `CLSID_DiaSource` ve arabirim kimliğiyle çağırarak elde edilir `IID_IDiaDataSource` . Örnek, bu arabirimin nasıl elde edilildiği gösterilmektedir.

## <a name="example"></a>Örnek

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
