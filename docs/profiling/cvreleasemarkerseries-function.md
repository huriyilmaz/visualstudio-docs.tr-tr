---
title: CvReleaseMarkerSeries İşlev | Microsoft Docs
description: Eşzamanlılık GörselleştiriciSI SDK'sı işlevi CvReleaseMarkerSeries (C kitaplığı) için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 20619133d217dff7e8992387a9fdc94a19f419d9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637161"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries işlevi
İşaretleyici serisini serbest bırakma. Serbest bıraktırdikten sonra işaretçi serisi nesnesini kullanma, aksi takdirde uygulama kilitlenmeye neden olabilir. İşaretleyici serisinin serbest bırakılama hatası bellek sızıntısına neden olur.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parametreler
 `pMarkerSeries` Sağlayıcı nesnesi değişkeninin adresi. Adres NULL olamaz, değişkenin herhangi bir değeri olabilir.

## <a name="return-value"></a>Dönüş Değeri
 S_OK serinin başarıyla yayımı veya herhangi bir hata durumunda hata kodu. Hata koşullarını kontrol etmek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)