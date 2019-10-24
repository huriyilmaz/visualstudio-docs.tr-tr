---
title: 'IDiaFrameData:: get_program | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 135f2b0a042dd74b573a0746831a48fb27e7c2a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743513"
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
 Başarılı olursa `S_OK`döndürür. Bu özellik desteklenmiyorsa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Program dizesi, bir prolog oluşturmak için yorumlanan bir makro dizisidir. Örneğin, tipik bir yığın çerçevesi `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`Program dizesini kullanabilir. Biçim, işleçlerin işlenenleri izlediği ters Lehçe gösterimidir. `T0` yığındaki geçici bir değişkeni temsil eder. Bu örnek aşağıdaki adımları gerçekleştirir:

1. Kayıt `ebp` içeriğini `T0`taşıyın.

2. Adres oluşturmak için `T0` değerine `4` ekleyin, bu adresten değeri alın ve kayıt `eip`değeri depolayın.

3. `T0` depolanan adresten değeri alın ve bu değeri yazmaç `ebp`olarak depolayın.

4. `T0` değerine `8` ekleyin ve bu değeri yazmaç `esp`olarak depolayın.

   Program dizesinin CPU 'ya ve geçerli yığın çerçevesi tarafından temsil edilen işlev için ayarlanan çağırma kuralına özel olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)