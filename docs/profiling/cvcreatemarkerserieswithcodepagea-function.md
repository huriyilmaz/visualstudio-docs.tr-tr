---
title: CvCreateMarkerSeriesWithCodePageA Işlevi | Microsoft Docs
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
ms.openlocfilehash: e17083c48db1ba1aa6b7ff45ee467ac97900e101
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332426"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA işlevi
Belirli bir sağlayıcı ve belirtilen kod sayfası için işaretleyici serisi oluşturur. Bu işlev, işaret API 'SI işlevleri tarafından yazılan metin için kod sayfasını açıkça belirtmek üzere kullanılabilir. Kod sayfasının ayarlanması, izlemenin yakalanıp farklı yerel ayarlara/dile sahip farklı makinelerde çözümlenme olasılığına karşı yararlı olabilir. Varsayılan olarak, GetACP () işlevi tarafından döndürülen kod sayfası kullanılır.

## <a name="syntax"></a>Söz dizimi

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametreler
 `pProvider`Sağlayıcı nesnesi daha önce CvInitProvider tarafından başlatıldı. NULL olamaz.

 `pSeriesName`İşaretleyici seri adı. NULL olamaz, ancak boş dizeye izin verilir.

 `nTextCodePage`Geçerli kod sayfası.

 `ppMarkerSeries`İşaretleyici serisi bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 İşaretleyici serisi başarıyla oluşturulduğunda S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvişaretleyiciler. h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)