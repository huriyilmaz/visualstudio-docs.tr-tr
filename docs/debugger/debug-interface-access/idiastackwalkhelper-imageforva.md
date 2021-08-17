---
description: Yürütülebilir dosyanın bellek alanı içinde bir yerde sanal adres verilen bir yürütülebilir dosya görüntüsünün bellekte başlangıcını döndürür.
title: IDiaStackWalkHelper::imageForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8ad55d62007c139f1a14e6c93b34797110b47557
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081312"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Yürütülebilir dosyanın bellek alanı içinde bir yerde sanal adres verilen bir yürütülebilir dosya görüntüsünün bellekte başlangıcını döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Parametreler
 `vaContext`

[in] Yürütülebilir dosyanın alanı içinde bir yerde yer alan sanal adres.

 `pvaImageStart`

[out] Yürütülebilir dosya görüntüsünün başlangıç sanal adresini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
