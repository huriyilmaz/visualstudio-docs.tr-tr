---
title: 'IDiaSourceFile:: get_checksum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f4367a7862dabe248dfbe08e64c45598abe3679
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741840"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Sağlama toplamı baytlarını alır.

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

'ndaki Veri arabelleğinin bayt cinsinden boyutu.

 `pcbData`

dışı Sağlama toplamı baytlarının sayısını döndürür. Bu parametre `NULL` olamaz.

 `data`

[in, out] Sağlama toplamı baytları ile doldurulmuş bir arabellek. Bu parametre `NULL`, `pcbData` gereken bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Sağlama toplamı baytları oluşturmak için kullanılan sağlama toplamı algoritmasının türünü öğrenmek için [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) yöntemini çağırın.

 Sağlama toplamı genellikle kaynak dosyanın görüntüsünden oluşturulur, böylece kaynak dosyadaki değişiklikler sağlama toplamı baytlarında değişikliklere yansıtılır. Sağlama toplamı baytları dosyanın yüklü görüntüsünden oluşturulmuş bir sağlama toplamıyla eşleşmiyorsa, dosyanın hasar görmüş veya ile oynanmış olarak kabul edilmesi gerekir.

 Tipik sağlama toplamı 32 bayttan fazla değil, ancak bir sağlama toplamı en büyük boyut olduğunu varsaymaz. Sağlama toplamını almak için gereken bayt sayısını almak için `data` parametresini `NULL` olarak ayarlayın. Ardından uygun boyutun bir arabelleğini ayırın ve bu yöntemi yeni arabellekle bir kez daha çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)