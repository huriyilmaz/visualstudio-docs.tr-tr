---
title: 'IDiaSourceFile:: get_checksumType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c6ce8f03534c3ed810e530dbd12d8c6d115be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741824"
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
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sağlama toplamı türü, sağlama algoritması ile eşleştirilenebilir bir değerdir. Örneğin, standart PDB dosya biçimi genellikle aşağıdaki değerlerden birine sahip olabilir:

|Sağlama toplamı türü|CryptoAPI etiketi|Açıklama|
|-------------------|---------------------|-----------------|
|0|\<none >|Sağlama yok.|
|1\.|`CALG_MD5`|MD5 karma algoritmasıyla üretilen sağlama toplamı.|
|2|`CALG_SHA1`|SHA1 karma algoritmasıyla oluşturulan sağlama toplamı.|

 @No__t_0 etiketleri `ALG_ID` numaralandırmadır. Karma algoritmalar hakkında daha fazla bilgi için Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] `CryptoAPI` bölümüne bakın.

 Kaynak dosyanın gerçek sağlama toplamı baytlarını elde etmek için [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)