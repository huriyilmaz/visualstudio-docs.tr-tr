---
description: IDiaStackWalkHelper::p ut_registerValue, yazmacın değerini ayarlar.
title: IDiaStackWalkHelper::p ut_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a93a21b10f6793cd75c6999998bc21b923ce69d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052325"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
Yazmanın değerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametreler
 `index`

[in] Yazmacı [belirten CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumeration enumeration değerinden bir değer.

 `NewVal`

[in] Yeni yazmaz değeri.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Değerin boyutuna rağmen, uygulama yalnızca yazmaca normal olarak nelerin sahip olduğunu depolamalı. Örneğin, bir 8 bit yazmalık, verilen değerin yalnızca en düşük 8 bitlerini tutar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e Numaralandırması](../../debugger/debug-interface-access/cv-hreg-e.md)
