---
description: Sembolün, C++ AMP Accelerator için derlenmiş kodda grup tarafından paylaşılan yerel değişkene karşılık gelen bir bayrağını alın.
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e334766cb5659d4f94c7db2f5fbdc0e4ab68a2ebb79e64a877c77c6e0a125dad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379873"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Sembolün, C++ AMP Accelerator için derlenmiş kodda grup tarafından paylaşılan yerel değişkene karşılık gelen bir bayrağını alın.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

[out] Sembolün, C++ AMP Accelerator için derlenmiş kodda grup paylaşılan yerel değişkenine `BOOL` karşılık gelen bir işaretçi. `TRUE`ise, `get_baseDataSlot` `get_baseDataOffset` değişkeninin depolama konumu bilgilerini almak için ve yöntemleri kullanılabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)
