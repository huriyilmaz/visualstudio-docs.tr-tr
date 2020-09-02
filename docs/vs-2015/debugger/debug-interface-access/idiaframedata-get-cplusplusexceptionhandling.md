---
title: 'IDiaFrameData:: get_cplusplusExceptionHandling | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_cplusplusExceptionHandling method
ms.assetid: 54ee9cde-ce8e-45f1-809c-6fbad800d850
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 12ccb2770cc15962f3899b99f14dd8c7f342c3cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553038"
---
# <a name="idiaframedataget_cplusplusexceptionhandling"></a>IDiaFrameData::get_cplusplusExceptionHandling
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C++ özel durum işlemenin etkin olup olmadığını gösteren bir bayrak alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı `TRUE` C++ özel durum işleme etkinse döndürür; Aksi takdirde, döndürür `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Yapılandırılmış özel durum işlemenin etkin olup olmadığını (C++ özel durum işlemenin çok farklı olduğunu) anlamak için, [IDiaFrameData:: get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md) yöntemini çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)
