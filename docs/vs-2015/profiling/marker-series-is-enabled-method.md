---
title: 'marker_series:: is_enabled yöntemi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ccef8ebbf63835a71027643b518280d5f4f867b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156407"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled Yöntemi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sağlayıcının herhangi bir oturumun etkinleştirilip etkinleştirilmediğini belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `_Importance`  
 Önem düzeyi.  
  
 `_Category`  
 Alan.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvmarkersobj. h  
  
 **Ad alanı:** Eşzamanlılık::d ıagstik  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [marker_series Sınıfı](../profiling/marker-series-class.md)
