---
title: CvCreateMarkerSeriesWithcodePageA Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b7e540e56ce0e97ac2c6aa2e42012569f9e4f272
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553077"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA fonksiyonu
Belirli bir sağlayıcı ve belirtilen kod sayfası için işaretleyici serisi oluşturur. Bu işlev, işaretçi API ANSI işlevleri tarafından yazılan metin için kod sayfasını açıkça belirtmek için kullanılabilir. İzlemenin yakalanması ve farklı yerel ayarlara/dillere sahip farklı makinelerde analiz edilmesi durumunda kod sayfasını ayarlamak yararlı olabilir. Varsayılan olarak GetACP() fonksiyonu tarafından döndürülen kod sayfası kullanılır.

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
 `pProvider`Sağlayıcı nesnesi daha önce CvInitProvider tarafından başolarak lanse edilir. NULL olamaz.

 `pSeriesName`İşaretleyici serisi adı. NULL olamaz, ancak boş dize izin verilir.

 `nTextCodePage`Geçerli kod sayfası.

 `ppMarkerSeries`Marker serisi bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK işaretleyici serisi başarıyla oluşturulduğunda veya herhangi bir hata olması durumunda hata kodu. Hata durumunu denetlemek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üstbilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)