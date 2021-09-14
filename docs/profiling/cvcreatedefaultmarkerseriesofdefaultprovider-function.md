---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider Işlevi | Microsoft Docs
description: CvCreateDefaultMarkerSeriesOfDefaultProvider (C Kitaplığı) Eşzamanlılık Görselleştiricisi SDK işlevi için başvuru bilgilerine bakın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637169"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider işlevi
Varsayılan bir sağlayıcının varsayılan işaretleyici serisini oluşturur.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametreler
 `ppProvider` Sağlayıcı nesne değişkeninin adresi. Adres NULL olamaz, değişken herhangi bir değere sahip olabilir.

 `ppMarkerSeries` İşaretleyici serisi nesne değişkeninin adresi. Adres NULL olamaz, değişken herhangi bir değere sahip olabilir.

## <a name="return-value"></a>Döndürülen değer
 Hem sağlayıcı hem de işaretleyici serisi başarıyla oluşturulduğunda S_OK ya da herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)