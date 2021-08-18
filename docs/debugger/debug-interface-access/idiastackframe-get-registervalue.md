---
description: Belirtilen kaydın değerini yığın çerçevesinde saklanan şekilde alır.
title: 'IDiaStackFrame:: get_registerValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e58f03a45b1fe680644c1bbc320383d6e3ac44ef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128858"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Belirtilen kaydın değerini yığın çerçevesinde saklanan şekilde alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `registerIndex`

'ndaki [CV_HREG_e sabit](../../debugger/debug-interface-access/cv-hreg-e.md) listesi numaralandırma değerlerinden biri.

 `pRetVal`

dışı Kasada depolanan değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e Numaralandırması](../../debugger/debug-interface-access/cv-hreg-e.md)
