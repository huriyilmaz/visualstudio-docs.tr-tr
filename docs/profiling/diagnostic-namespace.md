---
title: tanılama Namespace | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03671f314dca3c016f9524bcb246b74e0eb1f837
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970090"
---
# <a name="diagnostic-namespace"></a>tanılama ad alanı
Ad `diagnostics` alanı, EşzamanlıLık Görselleştirici işaretçileri yayan işlevsellik sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
namespace diagnostic;
```

## <a name="members"></a>Üyeler

### <a name="classes"></a>Sınıflar

|Adı|Açıklama|
|----------|-----------------|
|[marker_series Sınıfı](../profiling/marker-series-class.md)|Tek bir sağlayıcı tarafından oluşturulan olayların seri kanalını temsil eder.|
|[span Sınıfı](../profiling/span-class.md)|Uygulamanın bir aşamasını tanımlar.|

### <a name="enumerations"></a>Numaralandırmalar

|Adı|Açıklama|
|----------|-----------------|
|[marker_importance Sabit Listesi](../profiling/marker-importance-enumeration.md)|Eşzamanlı Görselleştirici işaretleyicisinin önem düzeyini temsil eder.|

## <a name="requirements"></a>Gereksinimler
 **Başlık:** *cvmarkersobj.h*

 **Ad alanı:** Eşzamanlılık

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlı ad alanı (Eşzamanlılık Görselleştiricisi)](../profiling/concurrency-namespace-concurrency-visualizer.md)