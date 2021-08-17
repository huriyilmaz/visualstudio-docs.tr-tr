---
description: Bu simge için derleyiciye özgü tür tanımlayıcı değerlerinin dizisini alır.
title: 'IDiaSymbol:: get_typeIds | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0324891d5819ea850d1a4cd21464778a93ea78ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036050"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Bu simge için derleyiciye özgü tür tanımlayıcı değerlerinin dizisini alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parametreler
 `cTypeIds`

'ndaki Verilerin tutulacağı arabelleğin boyutu.

 `pcTypeIds`

dışı `typeIds` Yazılan sayıyı veya varsa, `typeIds` `NULL` toplam tür tanımlayıcısı sayısını döndürür.

 `typeIds[]`

dışı Tür tanımlayıcılarıyla doldurulacak bir dizi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
