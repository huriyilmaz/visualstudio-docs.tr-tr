---
title: 'IDiaDataSource:: loadAndValidateDataFromPdb | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97afff946827c37ec2f84457016525377977dc8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744998"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Açılır ve program veritabanı (. pdb) dosyasının belirtilen imza bilgilerini eşleştirdiğini doğrular ve. pdb dosyasını hata ayıklama veri kaynağı olarak hazırlar.

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

'ndaki . Pdb dosyasının yolu.

`pcsig70`

'ndaki . Pdb dosya imzasına göre doğrulanacak GUID imzası. Yalnızca [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ve üzeri sürümlerde bulunan. pdb dosyalarının GUID imzaları vardır.

`sig`

'ndaki . Pdb dosya imzasına göre doğrulanacak 32 bitlik imza.

`age`

'ndaki Doğrulanacak yaş değeri. Yaş, bilinen bir zaman değerine karşılık gelmez; bir. pdb dosyasının karşılık gelen bir. exe dosyası ile eşitlenmemiş olup olmadığını anlamak için kullanılır.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Dosya açılamadı veya dosya geçersiz bir biçime sahip.|
|E_PDB_FORMAT|Eski biçimdeki bir dosyaya erişme girişiminde bulunuldu.|
|E_PDB_INVALID_SIG|İmza eşleşmiyor.|
|E_PDB_INVALID_AGE|Yaş eşleşmiyor.|
|E_INVALIDARG|Geçersiz parametre.|
|E_UNEXPECTED|Veri kaynağı zaten hazırlandı.|

## <a name="remarks"></a>Açıklamalar
Bir. pdb dosyası hem imza hem de yaş değerlerini içerir. Bu değerler. pdb dosyasıyla eşleşen. exe veya. dll dosyasında çoğaltılır. Bu yöntem, veri kaynağını hazırlamadan önce adlandırılan. pdb dosyasının imzasının ve Age değerinin belirtilen değerlerle eşleştiğini doğrular.

Bir. pdb dosyasını doğrulama olmadan yüklemek için [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodunu kullanın.

Veri yükleme işlemine (bir geri çağırma mekanizması aracılığıyla) erişim kazanmak için [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu kullanın.

Bir. pdb dosyasını doğrudan bellekten yüklemek için [IDiaDataSource:: Loaddatafromistreaı](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodunu kullanın.

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
