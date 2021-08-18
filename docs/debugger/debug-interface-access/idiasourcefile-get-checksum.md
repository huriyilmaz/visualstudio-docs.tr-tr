---
description: Sağlama toplam baytlarını alın.
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 972871513555feeb52b40086de58e619d7c7720c1540a4bfb7d5de419fd56ab6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344679"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Sağlama toplam baytlarını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametreler
 `cbData`

[in] Veri arabelleğinin bayt cinsinden boyutu.

 `pcbData`

[out] Sağlama toplam baytlarının sayısını döndürür. Bu parametre `NULL` olamaz.

 `data`

[in, out] Sağlama toplam baytları ile doldurulmuş bir arabellek. Bu parametre `NULL` ise, `pcbData` gereken bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sağlama toplam baytlarını oluşturmak için kullanılan sağlama toplam algoritmasının türünü belirlemek için [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) yöntemini arayın.

 Sağlama toplam değeri genellikle kaynak dosyanın görüntüsünden oluşturulur, bu nedenle kaynak dosyada yapılan değişiklikler sağlama toplam baytlarında yapılan değişikliklere yansıtıldı. Sağlama toplam baytları, dosyanın yüklenen görüntüsünden oluşturulan sağlama toplamları ile eşlenemse, dosyanın hasarlı veya üzerinde oynanmış olduğu kabul edilir.

 Tipik sağlama toplamlarının boyutu hiçbir zaman 32 bayttan fazla değildir, ancak sağlama toplamlarının en büyük boyutu olduğunu varsayma. Sağlama `data` toplamlarını `NULL` almak için gereken bayt sayısını almak için parametresini olarak ayarlayın. Ardından uygun boyutta bir arabellek ayırarak bu yöntemi yeni arabellekle bir kez daha arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
