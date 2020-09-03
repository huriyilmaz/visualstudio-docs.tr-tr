---
title: CvIsEnabled Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba30f3ab75504c0115b8a881f2014910f3b9fd0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177782"
---
# <a name="cvisenabled-function"></a>CvIsEnabled İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen ETW sağlayıcısını herhangi bir oturumun etkinleştirilip etkinleştirilmediğini belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `category`  
 Alan.  
  
 `level`  
 Önem düzeyi.  
  
 `pProvider`  
 Geçerli sağlayıcı nesnesi. NULL olamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Sağlayıcı Şu anda etkin ise S_OK. Sağlayıcı Şu anda devre dışıysa S_FALSE. Herhangi bir hata olması durumunda hata kodu. Hata durumunu denetlemek için başarısız makroyu kullanın ve ardından S_OK/S_FALSE kontrol edin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvişaretleyiciler. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)
