---
description: Kapsayan işlev için bir çerçeve verileri arabirimi alır.
title: 'IDiaFrameData:: get_functionParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7d453ec7e1c3731339eeb7bc3582e44bb2342624
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139606"
---
# <a name="idiaframedataget_functionparent"></a>IDiaFrameData::get_functionParent
Kapsayan işlev için bir çerçeve verileri arabirimi alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_functionParent ( 
   IDiaFrameData** pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Kapsayan işlev için bir [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
