---
title: 'span:: span Oluşturucusu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f761e87c1658c11bfdfd93a4f4e22299d88575a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979828"
---
# <a name="spanspan-constructor"></a>span::span Oluşturucusu

`span` sınıfının yeni bir örneğini başlatır.

## <a name="syntax"></a>Söz dizimi

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametreler

`_Series` Geçerli işaretleyici serisi bağlamı.

`_Format` Bağımsız değişken listesindeki nesnelere karşılık gelen sıfır veya daha fazla biçim öğesiyle metin içeren bir bileşik biçim dizesi.

`_Importance` Önem düzeyi.

`_Category` Alan.

## <a name="requirements"></a>Gereksinimler

**Üst bilgi:** *cvmarkersobj. h*

**Ad alanı:** Eşzamanlılık::d ıagstik

## <a name="see-also"></a>Ayrıca bkz.

- [span sınıfı](../profiling/span-class.md)