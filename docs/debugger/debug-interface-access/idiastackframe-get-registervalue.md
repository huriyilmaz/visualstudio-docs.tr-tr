---
description: Belirtilen yazmanın değerini yığın çerçevesinde depolandığı şekilde verir.
title: IDiaStackFrame::get_registerValue | Microsoft Docs
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628947"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Belirtilen yazmanın değerini yığın çerçevesinde depolandığı şekilde verir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `registerIndex`

[in] [Enumeration CV_HREG_e enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) değerlerinden biri.

 `pRetVal`

[out] Kayıtta depolanan değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e Numaralandırması](../../debugger/debug-interface-access/cv-hreg-e.md)
