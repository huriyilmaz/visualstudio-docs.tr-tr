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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4c5d32ec66b596510696bf81aa3bfc506047b54e64519304ca570a9ea88d39ca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240507"
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
