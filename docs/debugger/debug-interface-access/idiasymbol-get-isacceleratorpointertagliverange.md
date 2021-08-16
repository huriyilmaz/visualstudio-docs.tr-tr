---
description: Bir C++ AMP Accelerator için derlenmiş kodda işaretçi değişkeninin etiket bileşeni için sembolü tanım aralığı simgesine karşılık gelen bir bayrak alınır.
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0b42f2837113596b133dae93569645503bea91f2facc3200f15f5751716b8998
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454746"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Sembolün, C++ AMP Accelerator için derlenmiş  kodda bir işaretçi değişkeninin etiket bileşeni için tanım aralığı simgesine karşılık gelen bir bayrak alınır. Tanım aralığı simgesi, bir adres aralığı için değişkenin konumudür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] Sembolün tanım `BOOL` aralığı simgesine karşılık gelen bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
