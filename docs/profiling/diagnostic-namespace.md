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
ms.workload:
- multiple
ms.openlocfilehash: 22224e375c1d1f463f1c07d41ca5a03efa5cabdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923733"
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