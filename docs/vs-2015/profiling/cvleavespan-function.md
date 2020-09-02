---
title: CvLeaveSpan Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1f17de6df465408e9bec3b6db4e1620f0181fd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177761"
---
# <a name="cvleavespan-function"></a>CvLeaveSpan İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yayılımın sonunu işaretler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pSpan`  
 Önceki CvEnterSpan * çağrısıyla döndürülen span nesnesi. NULL olamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İleti başarıyla yazıldığında S_OK. Herhangi bir hata olması durumunda hata kodu. Hata koşulunu denetlemek için başarılı/başarısız makroları kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** cvişaretleyiciler. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ Kitaplığı başvurusu](../profiling/cpp-library-reference.md)
