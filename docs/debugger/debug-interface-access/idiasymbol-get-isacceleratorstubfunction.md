---
description: Simgenin bir parallel_for_each çağrısına karşılık gelen hızlandırıcı için derlenmiş bir gölgelendirici için en üst düzey işlev simgesine karşılık geldiğini gösterir.
title: 'IDiaSymbol:: get_isAcceleratorStubFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 710622fdb8fb10d0357c060097f13bab3be7d05f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156218"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Simgenin bir çağrıya karşılık gelen hızlandırıcı için derlenen bir gölgelendirici için üst düzey işlev simgesine karşılık geldiğini gösterir `parallel_for_each` .

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametreler
 `pFlag`

dışı `BOOL` Simgenin bir çağrıya karşılık gelen hızlandırıcı için derlenmiş bir gölgelendirici için üst düzey işlev simgesine karşılık geldiğini gösteren bir işaretçisi `parallel_for_each` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
