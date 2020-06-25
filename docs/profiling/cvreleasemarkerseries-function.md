---
title: CvReleaseMarkerSeries Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84db5dac77fbbc51c9f1c0e24173dcc8ca1d68c1
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332199"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries işlevi
Bırakma işaretçisi serisi. Bırakma işleminden sonra işaretleyici serisi nesnesi kullanmayın; aksi takdirde uygulama kilitlenebilir. İşaretleyici serisini serbest bırakma hatası, bellek sızıntısına neden olur.

## <a name="syntax"></a>Söz dizimi

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parametreler
 `pMarkerSeries`Sağlayıcı nesne değişkeninin adresi. Adres NULL olamaz, değişken herhangi bir değere sahip olabilir.

## <a name="return-value"></a>Dönüş Değeri
 İşaretleyici serisi ne zaman yayınlanmışsa S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)