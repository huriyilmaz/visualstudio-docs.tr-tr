---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741397"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Sanal adresle ilişkili PDATA veri bloğunu döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parametreler
 `va`

'ndaki Elde edilecek verilerin sanal adresini belirtir.

 `cbData`

'ndaki Elde edilecek verilerin bayt cinsinden boyutu.

 `pcbData`

dışı Alınan bayt cinsinden gerçek veri boyutunu döndürür.

 `pbData`

[in, out] İstenen verilerle doldurulmuş bir arabellek. @No__t_0 olamaz.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Belirtilen adres için PDATA yoksa `S_FALSE` döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir compiland 'nin PDATA (". pdata" adlı bölüm), işlevler için özel durum işleme hakkında bilgi içerir.

 Çağıranın ne kadar veri döndürüleceğini, çağıranın ne kadar veri olduğunu sorabilmesi için ne kadar veri döndürüleceğini bilir. Bu nedenle, `pbData` parametresi `NULL` bir hata döndürmesi için bu yöntemin uygulanması kabul edilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)