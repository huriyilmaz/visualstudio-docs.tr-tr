---
description: program veritabanı (.pdb) dosyasının sağlanan imza bilgileriyle eş olduğunu açar ve doğrular ve .pdb dosyasını hata ayıklama veri kaynağı olarak hazırlar.
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9a3d09b96f835b84399742a461b404bc4b75ddc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097949"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
program veritabanı (.pdb) dosyasının sağlanan imza bilgileriyle eş olduğunu açar ve doğrular ve .pdb dosyasını hata ayıklama veri kaynağı olarak hazırlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT loadAndValidateDataFromPdb ( 
   LPCOLESTR pdbPath,
   GUID*     pcsig70,
   DWORD     sig,
   DWORD     age
);
```

#### <a name="parameters"></a>Parametreler
`pdbPath`

[in] .pdb dosyasının yolu.

`pcsig70`

[in] .pdb dosya imzasını doğrulamak için GUID imzası. Yalnızca ve sonraki dosyalarda GUID imzaları olan .pdb [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] dosyaları.

`sig`

[in] .pdb dosya imzasını doğrulamak için 32 bit imza.

`age`

[in] Doğru için yaş değeri. Yaş her zaman bilinen bir saat değerine karşılık gelmez; bir .pdb dosyasının karşılık gelen bir dosyayla eşitlenen bir zaman .exe kullanılır.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri yer alır.

|Değer|Açıklama|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Dosya açılamadı veya dosyanın biçimi geçersiz.|
|E_PDB_FORMAT|Eski bir biçime sahip bir dosyaya erişmeye çalışıldı.|
|E_PDB_INVALID_SIG|İmza eşle değil.|
|E_PDB_INVALID_AGE|Yaş eşle değil.|
|E_ınvalıdarg|Geçersiz parametre.|
|E_unexpected|Veri kaynağı zaten hazırlanmıştır.|

## <a name="remarks"></a>Açıklamalar
.pdb dosyası hem imza hem de yaş değerlerini içerir. Bu değerler.pdb dosyasıyla .exe .dll dosyada çoğaltılır. Bu yöntem, veri kaynağını hazırlamadan önce, adlandırılmış .pdb dosyasının imzası ve yaşı değerlerinin sağlanan değerlerle eşle olduğunu doğrular.

Doğrulama olmadan bir .pdb dosyası yüklemek için [IDiaDataSource::loadDataFromPdb yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) kullanın.

Veri yükleme sürecine erişim elde etmek için (bir geri çağırma mekanizması aracılığıyla), [IDiaDataSource::loadDataForExe yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) kullanın.

.pdb dosyasını doğrudan bellekten yüklemek için [IDiaDataSource::loadDataFromIStream yöntemini](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) kullanın.

## <a name="example"></a>Örnek

```C++
IDiaDataSource* pSource;  // Previously created data source.
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);
DWORD expectedFileSignature = 0x12345678;
DWORD expectedAge           = 128;

HRESULT hr;
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",
                                          &expectedGUIDSignature,
                                          expectedFileSignature,
                                          expectedAge);
if (FAILED(hr))
{
    // Report an error
}

```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
