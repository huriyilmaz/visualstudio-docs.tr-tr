---
description: C++ AMP Accelerator için derlenmiş kodda işaretçi değişkeninin etiket bileşeninin tanım aralığı simgesine karşılık gelen sembolünü belirten bir bayrak C++ AMP alınır.
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
ms.openlocfilehash: b65e31e2e6d86711b576023ff0f70877e29cdd03
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031213"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
C++ AMP Accelerator için derlenmiş kodda işaretçi  değişkeninin etiket bileşeninin tanım aralığı simgesine karşılık gelen simgeyi belirten bir bayrak alınır. Tanım aralığı simgesi, bir adres aralığı için değişkenin konumudür.

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
