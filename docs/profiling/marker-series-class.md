---
title: marker_series Sınıfı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155d47f6764e754a1093cbcf884368c80d709a2a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62575923"
---
# <a name="marker_series-class"></a>marker_series sınıfı
Tek bir sağlayıcı tarafından oluşturulan olayların seri kanalını temsil eder.

## <a name="syntax"></a>Sözdizimi

```cpp
class marker_series;
```

## <a name="members"></a>Üyeler

### <a name="public-constructors"></a>Kamu yapıcılar

|Adı|Açıklama|
|----------|-----------------|
|[marker_series::marker_series yapıcı](../profiling/marker-series-marker-series-constructor.md)|`marker_series` sınıfının yeni bir örneğini başlatır.|
|[marker_series::~marker_series yıkıcı](../profiling/marker-series-tilde-marker-series-destructor.md)|marker_series nesneyi yok eder ve ayrılan tüm kaynakları salar.|

### <a name="public-methods"></a>Genel yöntemler

|Adı|Açıklama|
|----------|-----------------|
|[marker_series::is_enabled yöntemi](../profiling/marker-series-is-enabled-method.md)|Herhangi bir oturumun sağlayıcıyı etkinleştirip etkinleştirdiğini belirler.|
|[marker_series::write_alert yöntemi](../profiling/marker-series-write-alert-method.md)|Eşzamanlı Lık Görselleştiricisi izleme dosyasına bir uyarı yazar.|
|[marker_series::write_flag yöntemi](../profiling/marker-series-write-flag-method.md)|Eşzamanlı Görüntüleyici izleme dosyasına bir bayrak yazar.|
|[marker_series::write_message yöntemi](../profiling/marker-series-write-message-method.md)|Eşzamanlı Görüntüleyici izleme dosyasına bir ileti yazar.|

## <a name="inheritance-hierarchy"></a>Kalıtım hiyerarşisi
 `marker_series`

## <a name="requirements"></a>Gereksinimler
 **Başlık:** *cvmarkersobj.h*

 **Ad alanı:** Eşzamanlılık::diagnostik

## <a name="see-also"></a>Ayrıca bkz.
- [tanılama ad alanı](../profiling/diagnostic-namespace.md)