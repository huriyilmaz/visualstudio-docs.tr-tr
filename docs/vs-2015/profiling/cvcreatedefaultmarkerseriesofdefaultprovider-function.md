---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb0ab16dcd7e42a496317f4e7589bafdbdaf83dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162003"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan bir sağlayıcının varsayılan işaretleyici serisini oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppProvider`  
 Sağlayıcı nesne değişkeninin adresi. Adres NULL olamaz, değişken herhangi bir değere sahip olabilir.  
  
 `ppMarkerSeries`  
 İşaretleyici serisi nesne değişkeninin adresi. Adres NULL olamaz, değişken herhangi bir değere sahip olabilir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Hem sağlayıcı hem de işaretleyici serisi başarıyla oluşturulduğunda S_OK ya da herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvişaretleyiciler. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)
