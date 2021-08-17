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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091152"
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
 Bir derlemenin PDATA (".pdata" adlı bölümü), işlevler için özel durum işleme hakkında bilgi içerir.

 Çağıran ne kadar verinin döndürül olacağını bilir, bu nedenle çağıranın ne kadar veri kullanılabilir olduğunu sorması gerek yoktur. Bu nedenle, parametresi ise bu yöntemin uygulanması bir hata döndürür. `pbData` `NULL`

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
