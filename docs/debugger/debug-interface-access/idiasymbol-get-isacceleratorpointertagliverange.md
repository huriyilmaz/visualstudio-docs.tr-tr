---
description: simgenin bir C++ AMP hızlandırıcısı için derlenmiş koddaki bir işaretçi değişkeninin etiket bileşeni için açıklama aralığı simgesine karşılık geldiğini belirten bir bayrak alır.
title: 'IDiaSymbol:: get_isAcceleratorPointerTagLiveRange | Microsoft Docs'
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
simgenin bir C++ AMP hızlandırıcısı için derlenmiş koddaki bir işaretçi değişkeninin etiket bileşeni için *açıklama aralığı simgesine* karşılık geldiğini belirten bir bayrak alır. Tanım aralığı simgesi, bir adres yayılımı için bir değişkenin konumudur.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `BOOL` Simgenin, açıklama aralığı simgesine karşılık geldiğini gösteren bir işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
