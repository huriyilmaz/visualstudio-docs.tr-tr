---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d150e777f657fcf63dc66dbe3e686c1b445dd473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863811"
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

[in, out] İstenen verilerle doldurulmuş bir arabellek. Olamaz `NULL` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Belirtilen adres IÇIN PDATA yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir compiland 'nin PDATA (". pdata" adlı bölüm), işlevler için özel durum işleme hakkında bilgi içerir.

 Çağıranın ne kadar veri döndürüleceğini, çağıranın ne kadar veri olduğunu sorabilmesi için ne kadar veri döndürüleceğini bilir. Bu nedenle, parametresi bir hata döndürmek için bu yöntemin uygulanması kabul edilebilir `pbData` `NULL` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)