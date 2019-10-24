---
title: 'IDiaSymbol:: get_isAcceleratorStubFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baf71d3be8916c18b16e4022a2af884617b5fd70
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740312"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Simgenin bir `parallel_for_each` çağrısına karşılık gelen hızlandırıcı için derlenmiş bir gölgelendirici için en üst düzey işlev simgesine karşılık geldiğini gösterir.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı Bir `BOOL` işaretçisi, simgenin bir `parallel_for_each` çağrısına karşılık gelen hızlandırıcı için derlenmiş bir gölgelendirici için üst düzey işlev simgesine karşılık geldiğini belirtir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, `S_FALSE` veya bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)