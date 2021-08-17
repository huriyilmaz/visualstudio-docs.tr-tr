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
ms.openlocfilehash: b652591ea55aa7b25a95c12b1813c67c252fd817
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058741"
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
