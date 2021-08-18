---
description: Sağlama toplamı türünü alır.
title: 'IDiaSourceFile:: get_checksumType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7ed2d914bbd8c35e8d6f33a3cfe504a0ba40f9f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066191"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Sağlama toplamı türünü alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Sağlama toplamı türünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sağlama toplamı türü, sağlama algoritması ile eşleştirilenebilir bir değerdir. Örneğin, standart PDB dosya biçimi genellikle aşağıdaki değerlerden birine sahip olabilir:

|Sağlama toplamı türü|CryptoAPI etiketi|Açıklama|
|-------------------|---------------------|-----------------|
|0|\<none>|Sağlama yok.|
|1|`CALG_MD5`|MD5 karma algoritmasıyla üretilen sağlama toplamı.|
|2|`CALG_SHA1`|SHA1 karma algoritmasıyla oluşturulan sağlama toplamı.|

 `CryptoAPI`Etiketler `ALG_ID` numaralandırmadır. Karma algoritmalar hakkında daha fazla bilgi için Microsoft konusunun `CryptoAPI` bölümüne bakın [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] .

 Kaynak dosyanın gerçek sağlama toplamı baytlarını elde etmek için [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) metodunu çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
