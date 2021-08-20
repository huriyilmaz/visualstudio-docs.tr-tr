---
description: Span sınıfının yeni bir örneğini başlatır.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a1f3a073caa56dba1bc680a1e2205a7be0448f44
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157298"
---
# <a name="spanspan-constructor"></a>span::span Oluşturucusu

`span` sınıfının yeni bir örneğini başlatır.

## <a name="syntax"></a>Sözdizimi

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

- [Span sınıfı](../profiling/span-class.md)
