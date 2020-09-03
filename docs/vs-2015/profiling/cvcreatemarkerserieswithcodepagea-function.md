---
title: CvCreateMarkerSeriesWithCodePageA Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 635a872372ab775eceb00854a616884f3fc19fef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155527"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli bir sağlayıcı ve belirtilen kod sayfası için işaretleyici serisi oluşturur. Bu işlev, işaret API 'SI işlevleri tarafından yazılan metin için kod sayfasını açıkça belirtmek üzere kullanılabilir. Kod sayfasının ayarlanması, izlemenin yakalanıp farklı yerel ayarlara/dile sahip farklı makinelerde çözümlenme olasılığına karşı yararlı olabilir. Varsayılan olarak, GetACP () işlevi tarafından döndürülen kod sayfası kullanılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProvider`  
 Sağlayıcı nesnesi daha önce CvInitProvider tarafından başlatıldı. NULL olamaz.  
  
 `pSeriesName`  
 İşaretleyici seri adı. NULL olamaz, ancak boş dizeye izin verilir.  
  
 `nTextCodePage`  
 Geçerli kod sayfası.  
  
 `ppMarkerSeries`  
 İşaretleyici serisi bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İşaretleyici serisi başarıyla oluşturulduğunda S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvişaretleyiciler. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)
