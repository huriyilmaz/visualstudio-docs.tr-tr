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
ms.openlocfilehash: 5c5d23e1702ed9fa928ad0459255639c454af2da15e9ce169211c607757e487a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454882"
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
