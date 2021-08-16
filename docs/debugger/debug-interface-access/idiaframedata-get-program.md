---
description: Geçerli işleve yapılan çağrıdan önce kayıt kümesi hesaplamak için kullanılan program dizesini alır.
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 22946c85ecb74a54a4e4ff844ff7b0f8359bbf62bee78aeda108a33342ac60c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392307"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Geçerli işleve yapılan çağrıdan önce kayıt kümesi hesaplamak için kullanılan program dizesini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

[out] Program dizesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Bu `S_FALSE` özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Program dizesi, prolog'u kurmak için yorumlanır bir makro dizisidir. Örneğin, tipik bir yığın çerçevesi program dizesini `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` kullanabilir. Biçim, işleçlerin işlenenleri takip etmek için ters lehçe biçimidir. `T0` , yığında geçici bir değişkeni temsil eder. Bu örnek aşağıdaki adımları gerçekleştirir:

1. Yazmanın içeriğini klasörüne `ebp` `T0` taşıma.

2. bir adres üretmek, bu adresten değeri almak ve değeri register içinde depolamak için içinde `4` `T0` değerine `eip` ekleyin.

3. içinde depolanan adresten değeri elde edin `T0` ve bu değeri register içinde depolar. `ebp`

4. değerine `8` ekleyin ve bu değeri register içinde `T0` `esp` depolar.

   Program dizesinin CPU'ya ve geçerli yığın çerçevesiyle temsil edilen işlev için ayarlanmış çağırma kuralına özgü olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
