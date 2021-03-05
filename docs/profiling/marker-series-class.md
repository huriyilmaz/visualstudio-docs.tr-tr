---
description: Tek bir sağlayıcı tarafından oluşturulan olayların seri kanalını temsil eder.
title: marker_series sınıfı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4df579ff4eb43dfca4c386716c49f12dae04e9fa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223621"
---
# <a name="marker_series-class"></a>marker_series sınıfı
Tek bir sağlayıcı tarafından oluşturulan olayların seri kanalını temsil eder.

## <a name="syntax"></a>Syntax

```cpp
class marker_series;
```

## <a name="members"></a>Üyeler

### <a name="public-constructors"></a>Ortak oluşturucular

|Ad|Açıklama|
|----------|-----------------|
|[marker_series:: marker_series Oluşturucusu](../profiling/marker-series-marker-series-constructor.md)|`marker_series` sınıfının yeni bir örneğini başlatır.|
|[marker_series:: ~ marker_series yok edici](../profiling/marker-series-tilde-marker-series-destructor.md)|Marker_series nesnesini yok eder ve tüm ayrılmış kaynakları serbest bırakır.|

### <a name="public-methods"></a>Ortak Yöntemler

|Ad|Açıklama|
|----------|-----------------|
|[marker_series:: is_enabled yöntemi](../profiling/marker-series-is-enabled-method.md)|Sağlayıcının herhangi bir oturumun etkinleştirilip etkinleştirilmediğini belirler.|
|[marker_series:: write_alert yöntemi](../profiling/marker-series-write-alert-method.md)|Eşzamanlılık görselleştiricisi izleme dosyasına bir uyarı yazar.|
|[marker_series:: write_flag yöntemi](../profiling/marker-series-write-flag-method.md)|Eşzamanlılık görselleştiricisi izleme dosyasına bir bayrak yazar.|
|[marker_series:: write_message yöntemi](../profiling/marker-series-write-message-method.md)|Eşzamanlılık görselleştiricisi izleme dosyasına bir ileti yazar.|

## <a name="inheritance-hierarchy"></a>Devralma hiyerarşisi
 `marker_series`

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkersobj. h*

 **Ad alanı:** Eşzamanlılık::d ıagstik

## <a name="see-also"></a>Ayrıca bkz.
- [Tanılama ad alanı](../profiling/diagnostic-namespace.md)
