---
description: Span sınıfının yeni bir örneğini başlatılır.
title: span::span Oluşturucu | Microsoft Docs
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
ms.openlocfilehash: 8f399ee3d0c5243f5bc9451ff7d6b3f264ca5814a818153301b72d68d14e3684
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410248"
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

`_Series` Geçerli işaretçi serisi bağlamı.

`_Format` Bağımsız değişken listesinde nesnelere karşılık gelen sıfır veya daha fazla biçim öğeleriyle kesişen metin içeren bileşik biçim dizesi.

`_Importance` Önem düzeyi.

`_Category` Kategori.

## <a name="requirements"></a>Gereksinimler

**Üst bilgi:** *cvmarkersobj.h*

**Ad alanı:** Concurrency::d iagnostic

## <a name="see-also"></a>Ayrıca bkz.

- [span sınıfı](../profiling/span-class.md)
