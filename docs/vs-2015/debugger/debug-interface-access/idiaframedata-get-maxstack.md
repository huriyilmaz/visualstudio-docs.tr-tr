---
title: 'IDiaFrameData:: get_maxStack | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bacefc74c4699ef2d2d75ff7ca7af47a56cfb44b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562895"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çerçevedeki yığına gönderilen en fazla bayt sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Yığına gönderilen en fazla bayt sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin döndürdüğü değer genellikle program dizesinin yorumu içinde kullanılır (program dizesinin tanımı için [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) metoduna bakın).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
