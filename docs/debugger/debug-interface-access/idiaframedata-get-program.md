---
description: Geçerli işleve yapılan çağrıdan önce kayıt kümesini hesaplamak için kullanılan program dizesini alır.
title: 'IDiaFrameData:: get_program | Microsoft Docs'
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629822"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Geçerli işleve yapılan çağrıdan önce kayıt kümesini hesaplamak için kullanılan program dizesini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Program dizesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Program dizesi, bir prolog oluşturmak için yorumlanan bir makro dizisidir. Örneğin, tipik bir yığın çerçevesi Program dizesini kullanabilir `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Biçim, işleçlerin işlenenleri izlediği ters Lehçe gösterimidir. `T0` yığında geçici bir değişkeni temsil eder. Bu örnek aşağıdaki adımları gerçekleştirir:

1. Kayıt içeriğini içine taşıyın `ebp` `T0` .

2. `4` `T0` Bir adres oluşturmak, bu adresten değeri almak ve kayıt sırasında değeri depolamak için içindeki değerine ekleyin `eip` .

3. İçinde depolanan adresten değeri alın `T0` ve bu değeri kayıt ' de saklayın `ebp` .

4. `8`İçindeki değerine ekleyin `T0` ve bu değeri yazmaç içinde depolayın `esp` .

   Program dizesinin CPU 'ya ve geçerli yığın çerçevesi tarafından temsil edilen işlev için ayarlanan çağırma kuralına özel olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
