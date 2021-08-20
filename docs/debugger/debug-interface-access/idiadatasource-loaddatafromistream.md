---
description: Bellek içinde veri akışı aracılığıyla erişilen bir program veritabanı (.pdb) dosyasında depolanan hata ayıklama verilerini hazırlar.
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 005c423df13f2d1b906a229665c79d6ee52627a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113763"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Bellek içinde veri akışı aracılığıyla erişilen bir program veritabanı (.pdb) dosyasında depolanan hata ayıklama verilerini hazırlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Parametreler
 pIStream

[in] Kullanmak <xref:IStream> üzere veri akışını temsil eden nesne.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri yer alır.

|Değer|Açıklama|
|-----------|-----------------|
|E_PDB_FORMAT|Eski bir biçime sahip bir dosyaya erişmeye çalışıldı.|
|E_ınvalıdarg|Geçersiz parametre.|
|E_unexpected|Veri kaynağı zaten hazırlanmıştır.|

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yürütülebilir dosyanın hata ayıklama verilerini bir nesnesi aracılığıyla bellekten elde <xref:IStream> edek sağlar.

 Doğrulama olmadan bir .pdb dosyası yüklemek için [IDiaDataSource::loadDataFromPdb yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) kullanın.

 .pdb dosyasını belirli ölçütlere göre doğrulamak için [IDiaDataSource::loadAndValidateDataFromPdb yöntemini](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) kullanın.

 Veri yükleme sürecine erişim elde etmek için (bir geri çağırma mekanizması aracılığıyla), [IDiaDataSource::loadDataForExe yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
