---
title: CvCreateMarkerSeriesWithCodePageA Işlevi | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi SDK işlevi CvCreateMarkerSeriesWithCodePageA (C Kitaplığı) için başvuru bilgilerine bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f4f19df03c4c2f6bb21a5e2262a4a1495adab8
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686161"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA işlevi
Belirli bir sağlayıcı ve belirtilen kod sayfası için işaretleyici serisi oluşturur. Bu işlev, işaret API 'SI işlevleri tarafından yazılan metin için kod sayfasını açıkça belirtmek üzere kullanılabilir. Kod sayfasının ayarlanması, izlemenin yakalanıp farklı yerel ayarlara/dile sahip farklı makinelerde çözümlenme olasılığına karşı yararlı olabilir. Varsayılan olarak, GetACP () işlevi tarafından döndürülen kod sayfası kullanılır.

## <a name="syntax"></a>Sözdizimi

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametreler
 `pProvider` Sağlayıcı nesnesi daha önce CvInitProvider tarafından başlatıldı. NULL olamaz.

 `pSeriesName` İşaretleyici seri adı. NULL olamaz, ancak boş dizeye izin verilir.

 `nTextCodePage` Geçerli kod sayfası.

 `ppMarkerSeries` İşaretleyici serisi bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 İşaretleyici serisi başarıyla oluşturulduğunda S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)