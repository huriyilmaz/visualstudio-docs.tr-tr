---
title: 'IDiaSourceFile:: get_uniqueId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30a210c12384cbde55dafe6f3410b8fc840e8507
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741787"
---
# <a name="idiasourcefileget_uniqueid"></a>IDiaSourceFile::get_uniqueId
Bu görüntü için benzersiz bir basit tamsayı anahtar değeri alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_uniqueId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bu görüntü için benzersiz olan bir basit tamsayı anahtar değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dizeler yerine anahtarları karşılaştırma, satır numarası işlemeyi hızlandırabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)