---
description: Hata ayıklama sembollerinin kaynağına erişimi başlatma.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2c524025a5117406ad8de3737226495253f297e9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630476"
---
# <a name="idiadatasource"></a>IDiaDataSource
Hata ayıklama sembollerinin kaynağına erişimi başlatma.

## <a name="syntax"></a>Syntax

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaDataSource` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Son yükleme hatasının dosya adını alır.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Program veritabanı (.pdb) dosyasını açar ve hata ayıklama veri kaynağı olarak hazırlar.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|açar ve program veritabanı (.pdb) dosyasının sağlanan imza bilgileriyle eş olduğunu doğrular; .pdb dosyasını hata ayıklama veri kaynağı olarak hazırlar.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|/.exedosyasıyla ilişkili hata .dll hazırlar.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Bellek içinde veri akışı aracılığıyla erişilen bir program veritabanı (.pdb) dosyasında depolanan hata ayıklama verilerini hazırlar.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Sembolleri sorgulamak için bir oturum açar.|

## <a name="remarks"></a>Açıklamalar
Arabirimin yükleme yöntemlerinden biri çağrısı `IDiaDataSource` sembol kaynağını açar. [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) yöntemine yapılan başarılı bir çağrı, veri kaynağını sorgulamayı destekleyen [bir IDiaSession](../../debugger/debug-interface-access/idiasession.md) arabirimi döndürür. Yükleme yöntemi dosyayla ilgili bir hata döndürürse [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) yöntemi dönüş değeri hatayla ilişkili dosya adını içerir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, sınıf tanımlayıcısı ve `CoCreateInstance` arabirim kimliği ile işlevi `CLSID_DiaSource` çağrılarak elde `IID_IDiaDataSource` edilir. Örnek, bu arabirimin nasıl alınarak elde edilenleri gösterir.

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
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
