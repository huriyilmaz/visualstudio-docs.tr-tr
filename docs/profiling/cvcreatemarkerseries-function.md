---
title: CvCreateMarkerSeries İşlev | Microsoft Docs
description: Eşzamanlılık Görselleştirici SDK'sı işlevi CvCreateMarkerSeries (C kitaplığı) için başvuru bilgilerine bakın.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6ace7287bfbb12d078e8dcbc846042f8394215f1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076769"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries işlevi
Belirtilen sağlayıcı için işaretçi serisi oluşturur.

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
 `pProvider` Daha önce CvInitProvider tarafından başlatılan provider nesnesi. NULL olamaz.

 `pSeriesName` İşaretçi serisi adı. NULL olamaz ancak boş dizeye izin verilir.

 `ppMarkerSeries` İşaretçi serisi bağlamını depolanacak çıkış değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK seri başarıyla oluşturulduğunda veya herhangi bir hata olduğunda hata kodu. Hata koşullarını kontrol etmek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)