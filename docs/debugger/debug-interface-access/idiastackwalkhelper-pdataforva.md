---
description: Sanal adresle ilişkili PDATA veri bloğunü döndürür.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c2267173539401f9b673a6cf760abe9070279970
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626817"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Sanal adresle ilişkili PDATA veri bloğunü döndürür.

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

[in] Elde edilen verilerin sanal adresini belirtir.

 `cbData`

[in] Elde edilen verilerin bayt cinsinden boyutu.

 `pcbData`

[out] Elde edilen verilerin gerçek boyutunu bayt cinsinden döndürür.

 `pbData`

[in, out] İstenen verilerle doldurulmuş bir arabellek. olamaz. `NULL`

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür. Belirtilen `S_FALSE` adres için PDATA yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir derlemenin PDATA 'sı (".pdata" adlı bölüm), işlevler için özel durum işleme hakkında bilgi içerir.

 Çağıran ne kadar verinin döndürül olacağını bilir, bu nedenle çağıranın ne kadar veri kullanılabilir olduğunu sorması gerek yoktur. Bu nedenle, parametresi ise bu yöntemin uygulanması bir hata döndürür. `pbData` `NULL`

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
