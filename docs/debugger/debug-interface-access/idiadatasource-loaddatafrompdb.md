---
description: Program veritabanı (.pdb) dosyasını açar ve hata ayıklama veri kaynağı olarak hazırlar.
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 053a09d770069bc0030025fb6be130276b9942d327dc971b400e7a434e038a2c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345255"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Program veritabanı (.pdb) dosyasını açar ve hata ayıklama veri kaynağı olarak hazırlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parametreler
pdbPath

[in] .pdb dosyasının yolu.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri yer alır.

|Değer|Açıklama|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Dosya açılamadı veya dosyanın geçersiz bir biçime sahip olduğu belirlendi.|
|E_PDB_FORMAT|Eski bir biçime sahip bir dosyaya erişmeye çalışıldı.|
|E_ınvalıdarg|Geçersiz parametre.|
|E_unexpected|Veri kaynağı zaten hazırlanmıştır.|

## <a name="remarks"></a>Açıklamalar
Bu yöntem, hata ayıklama verilerini doğrudan bir .pdb dosyasından yükler.

.pdb dosyasını belirli ölçütlere göre doğrulamak için [IDiaDataSource::loadAndValidateDataFromPdb yöntemini](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) kullanın.

Veri yükleme sürecine erişim elde etmek için (bir geri çağırma mekanizması aracılığıyla), [IDiaDataSource::loadDataForExe yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) kullanın.

.pdb dosyasını doğrudan bellekten yüklemek için [IDiaDataSource::loadDataFromIStream yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) kullanın.

## <a name="example"></a>Örnek

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
