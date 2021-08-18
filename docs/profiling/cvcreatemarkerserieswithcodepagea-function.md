---
title: CvCreateMarkerSeriesWithCodePageA İşlev | Microsoft Docs
description: Eşzamanlılık Görselleştirici SDK'sı işlevi CvCreateMarkerSeriesWithCodePageA (C kitaplığı) için başvuru bilgilerine bakın.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 187cc85b3bcdb552a491dd20e866a9f02e025fd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084538"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA işlevi
Belirli bir sağlayıcı ve belirtilen kod sayfası için işaretçi serisi oluşturur. Bu işlev, işaretçi API'si ANSI işlevleri tarafından yazılan metin için kod sayfasını açıkça belirtmek için kullanılabilir. Kod sayfasını ayarlama, izlemenin yakalanıp farklı yerel ayarlara/dillere sahip farklı makinelerde analiz olması durumunda yararlı olabilir. Varsayılan olarak GetACP() işlevi tarafından döndürülen kod sayfası kullanılır.

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
 `pProvider` Daha önce CvInitProvider tarafından başlatılan provider nesnesi. NULL olamaz.

 `pSeriesName` İşaretçi serisi adı. NULL olamaz ancak boş dizeye izin verilir.

 `nTextCodePage` Geçerli kod sayfası.

 `ppMarkerSeries` İşaretçi serisi bağlamını depolanacak çıkış değişkeninin adresi. NULL olamaz.

## <a name="return-value"></a>Döndürülen değer
 S_OK seri başarıyla oluşturulduğunda veya herhangi bir hata olduğunda hata kodu. Hata koşullarını kontrol etmek için BAŞARILI/BAŞARILI makroları kullanın.

## <a name="requirements"></a>Gereksinimler
 **Üst bilgi:** *cvmarkers.h*

## <a name="see-also"></a>Ayrıca bkz.
- [C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)