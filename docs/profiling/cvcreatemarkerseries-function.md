---
title: CvCreateMarkerSeries Işlevi | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi SDK işlevi CvCreateMarkerSeries (C Kitaplığı) için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941040"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries işlevi
Belirli bir sağlayıcı için işaretleyici serisi oluşturur.

## <a name="syntax"></a>Sözdizimi

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>Parametreler
 `pProvider` Sağlayıcı nesnesi daha önce CvInitProvider tarafından başlatıldı. NULL olamaz.

 `pSeriesName` İşaretleyici seri adı. NULL olamaz, ancak boş dizeye izin verilir.

 `ppMarkerSeries` İşaretleyici serisi bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 İşaretleyici serisi başarıyla oluşturulduğunda S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)