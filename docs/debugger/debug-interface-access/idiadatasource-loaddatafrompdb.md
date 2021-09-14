---
description: Bir program veritabanı (. pdb) dosyasını açıp hata ayıklama veri kaynağı olarak hazırlar.
title: 'IDiaDataSource:: loadDataFromPdb | Microsoft Docs'
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
ms.openlocfilehash: 957cee1c9694f31f0fecd2123d7b4d7fdf104df5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630483"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Bir program veritabanı (. pdb) dosyasını açıp hata ayıklama veri kaynağı olarak hazırlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parametreler
pdbPath

'ndaki . Pdb dosyasının yolu.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Dosya açılamadı veya dosyanın biçimi geçersiz olduğundan belirlendi.|
|E_PDB_FORMAT|Eski biçimdeki bir dosyaya erişme girişiminde bulunuldu.|
|E_INVALIDARG|Geçersiz parametre.|
|E_UNEXPECTED|Veri kaynağı zaten hazırlandı.|

## <a name="remarks"></a>Açıklamalar
Bu yöntem, hata ayıklama verilerini doğrudan bir. pdb dosyasından yükler.

. Pdb dosyasını belirli ölçütlere karşı doğrulamak için [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodunu kullanın.

Veri yükleme işlemine (bir geri çağırma mekanizması aracılığıyla) erişim kazanmak için [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu kullanın.

Bir. pdb dosyasını doğrudan bellekten yüklemek için [IDiaDataSource:: Loaddatafromistreaı](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodunu kullanın.

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
