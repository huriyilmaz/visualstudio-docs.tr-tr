---
title: Tanılama ad alanı | Microsoft Docs
description: Eşzamanlılık görselleştiricisi işaretçilerini göstermek için tanılama ad alanını kullanın. Tanılama ad alanı eşzamanlılık ad alanının bir üyesidir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9e9d976983b534081926795ff1754fe7047f2f42
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142071"
---
# <a name="diagnostic-namespace"></a>Tanılama ad alanı
`diagnostics`Ad alanı eşzamanlılık görselleştiricisi işaretçilerini yayma işlevlerini sağlar.

## <a name="syntax"></a>Syntax

```cpp
namespace diagnostic;
```

## <a name="members"></a>Üyeler

### <a name="classes"></a>Sınıflar

|Ad|Açıklama|
|----------|-----------------|
|[marker_series Sınıfı](../profiling/marker-series-class.md)|Tek bir sağlayıcı tarafından oluşturulan olayların seri kanalını temsil eder.|
|[span Sınıfı](../profiling/span-class.md)|Uygulamanın aşamasını tanımlar.|

### <a name="enumerations"></a>Listelemeler

|Ad|Açıklama|
|----------|-----------------|
|[marker_importance Numaralandırması](../profiling/marker-importance-enumeration.md)|Bir eşzamanlılık görselleştiricisi işaretçisinin önem derecesini temsil eder.|

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj. h*

 **Ad alanı:** Zamanlı

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık ad alanı (eşzamanlılık görselleştiricisi)](../profiling/concurrency-namespace-concurrency-visualizer.md)