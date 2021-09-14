---
description: Sağlama alma türü alınır.
title: IDiaSourceFile::get_checksumType | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629042"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Sağlama alma türü alınır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Sağlamam türünü döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sağlamam türü, sağlama sağlama algoritmasıyla eşlenen bir değerdir. Örneğin, standart PDB dosya biçimi genellikle aşağıdaki değerlerden birini kullanabilir:

|Sağlamam Türü|CryptoAPI Etiketi|Açıklama|
|-------------------|---------------------|-----------------|
|0|\<none>|Sağlama sağlamaları yok.|
|1|`CALG_MD5`|MD5 karma algoritmasıyla oluşturulan checksum.|
|2|`CALG_SHA1`|SHA1 karma algoritmasıyla oluşturulan checksum.|

 Etiketler, `CryptoAPI` `ALG_ID` numaralamadandır. Karma algoritmaları hakkında daha fazla bilgi için `CryptoAPI` Microsoft 'un bölümüne [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] bakın.

 Kaynak dosyanın gerçek sağlama toplam baytlarını almak için [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
