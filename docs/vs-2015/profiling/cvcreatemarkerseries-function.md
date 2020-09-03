---
title: CvCreateMarkerSeries Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dc4af6ef3b2ffc89ec0e69a6dd63923f5c55ffe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155540"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli bir sağlayıcı için işaretleyici serisi oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
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
 `pProvider`  
 Sağlayıcı nesnesi daha önce CvInitProvider tarafından başlatıldı. NULL olamaz.  
  
 `pSeriesName`  
 İşaretleyici seri adı. NULL olamaz, ancak boş dizeye izin verilir.  
  
 `ppMarkerSeries`  
 İşaretleyici serisi bağlamını depolayacak bir çıktı değişkeninin adresi. NULL olamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İşaretleyici serisi başarıyla oluşturulduğunda S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvişaretleyiciler. h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)
