---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150083"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sanal adresle ilişkili PDATA veri bloğunu döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `va`  
 'ndaki Elde edilecek verilerin sanal adresini belirtir.  
  
 `cbData`  
 'ndaki Elde edilecek verilerin bayt cinsinden boyutu.  
  
 `pcbData`  
 dışı Alınan bayt cinsinden gerçek veri boyutunu döndürür.  
  
 `pbData`  
 [in, out] İstenen verilerle doldurulmuş bir arabellek. Olamaz `NULL` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Belirtilen adres IÇIN PDATA yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir compiland 'nin PDATA (". pdata" adlı bölüm), işlevler için özel durum işleme hakkında bilgi içerir.  
  
 Çağıranın ne kadar veri döndürüleceğini, çağıranın ne kadar veri olduğunu sorabilmesi için ne kadar veri döndürüleceğini bilir. Bu nedenle, parametresi bir hata döndürmek için bu yöntemin uygulanması kabul edilebilir `pbData` `NULL` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
