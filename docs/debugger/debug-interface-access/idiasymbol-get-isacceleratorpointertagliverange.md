---
description: Simgenin bir C++ AMP Hızlandırıcısı için derlenmiş koddaki bir işaretçi değişkeninin etiket bileşeni için açıklama aralığı simgesine karşılık geldiğini belirten bir bayrak alır.
title: 'IDiaSymbol:: get_isAcceleratorPointerTagLiveRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f46618e0dddf788f106cfccd836d3e228835735
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156246"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Simgenin bir C++ AMP Hızlandırıcısı için derlenmiş koddaki bir işaretçi değişkeninin etiket bileşeni için *Açıklama aralığı simgesine* karşılık geldiğini belirten bir bayrak alır. Tanım aralığı simgesi, bir adres yayılımı için bir değişkenin konumudur.

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
