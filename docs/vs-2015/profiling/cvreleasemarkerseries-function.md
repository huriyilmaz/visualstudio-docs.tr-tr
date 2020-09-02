---
title: CvReleaseMarkerSeries Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bfa9952a834110ef0fea36568ea210b637547aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177749"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bırakma işaretçisi serisi. Bırakma işleminden sonra işaretleyici serisi nesnesi kullanmayın; aksi takdirde uygulama kilitlenebilir. İşaretleyici serisini serbest bırakma hatası, bellek sızıntısına neden olur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pMarkerSeries`  
 Sağlayıcı nesne değişkeninin adresi. Adres NULL olamaz, değişken herhangi bir değere sahip olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İşaretleyici serisi ne zaman yayınlanmışsa S_OK veya herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvişaretleyiciler. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)
