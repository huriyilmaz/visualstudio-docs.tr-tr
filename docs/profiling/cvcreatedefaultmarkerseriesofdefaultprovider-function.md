---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider İşlev | Microsoft Docs
description: Eşzamanlılık Görselleştirici SDK'sı işlevi CvCreateDefaultMarkerSeriesOfDefaultProvider (C kitaplığı) için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 82d38199007cdc906361e4beb76d1e2334a0ba4e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084564"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider işlevi
Varsayılan sağlayıcının varsayılan işaretçi serisini oluşturur.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametreler
 `ppProvider` Sağlayıcı nesnesi değişkeninin adresi. Adres NULL olamaz, değişkenin herhangi bir değeri olabilir.

 `ppMarkerSeries` İşaretçi serisi nesne değişkeninin adresi. Adres NULL olamaz, değişkenin herhangi bir değeri olabilir.

## <a name="return-value"></a>Döndürülen değer
 S_OK hem sağlayıcı hem de işaretçi serisi başarıyla oluşturulduğunda veya herhangi bir hata olduğunda hata kodu. Hata koşullarını kontrol etmek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)