---
title: CvReleaseMarkerSeries Işlevi | Microsoft Docs
description: CvReleaseMarkerSeries (C Kitaplığı) Eşzamanlılık Görselleştiricisi SDK işlevi için başvuru bilgilerine bakın.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084501"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries işlevi
Bırakma işaretçisi serisi. Bırakma işleminden sonra işaretleyici serisi nesnesi kullanmayın; aksi takdirde uygulama kilitlenebilir. İşaretleyici serisini serbest bırakma hatası, bellek sızıntısına neden olur.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parametreler
 `pMarkerSeries` Sağlayıcı nesne değişkeninin adresi. Adres NULL olamaz, değişken herhangi bir değere sahip olabilir.

## <a name="return-value"></a>Dönüş Değeri
 İşaretleyici serisi ne zaman yayınlanmışsa S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)