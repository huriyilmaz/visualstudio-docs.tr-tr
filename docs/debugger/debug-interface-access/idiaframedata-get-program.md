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
ms.openlocfilehash: e78315ba7fe4f4de3ae94cafe6d8ffa78ef32065
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036418"
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

1. Yazmanın içeriğini 'ye `ebp` `T0` taşıma.

2. bir adres üretmek, bu adresten değeri almak ve değeri register içinde depolamak için içinde `4` `T0` değerine `eip` ekleyin.

3. içinde depolanan adresten değeri elde edin `T0` ve bu değeri register içinde depolar. `ebp`

4. değerini `8` içinde değerine ekleyin `T0` ve bu değeri register içinde `esp` depolar.

   Program dizesinin CPU'ya ve geçerli yığın çerçevesiyle temsil edilen işlev için ayarlanmış çağırma kuralına özgü olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
