---
description: IDiaStackWalkFrame::p ut_registerValue, yazmacın değerini ayarlar.
title: IDiaStackWalkFrame::p ut_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 639b57d876cd4ced7bf6ab458af7b43dcadb6a4e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091168"
---
# <a name="idiastackwalkframeput_registervalue"></a>IDiaStackWalkFrame::put_registerValue
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

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [CV_HREG_e Numaralandırması](../../debugger/debug-interface-access/cv-hreg-e.md)
