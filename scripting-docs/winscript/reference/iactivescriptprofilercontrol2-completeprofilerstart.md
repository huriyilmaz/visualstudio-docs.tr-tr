---
title: 'Iactivescriptprofilercontrol2:: CompleteProfilerStart | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571561"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Profil oluşturucuyu, uygulanabilir tüm betik altyapılarında profil oluşturmayı başlattığınız şekilde bildirir. Bu yöntemi kullanarak, profil oluşturmaya başladığınızda [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] çalışıyorsa, tüm çağrı yığınını elde edebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yöntem herhangi bir parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş değeri|Anlamı|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Profil oluşturma başlatılamıyor.|  
|`S_FALSE`|Bir betik çalışmadığı zaman profil oluşturma işlemi başlatıldı.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profil oluşturma etkin değil. Hiçbir geri arama ayarlanmadı.|  
|`E_OUTOFMEMORY`|Bellek dışı bir durum nedeniyle çağrı yığını alınamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IActiveScriptProfilerControl2::CompleteProfilerStart` çağırmak, çağrı yığınında bulunan işlevlerin olaylarının gönderilmesini sağlar. Bu yöntem, geçerli sekmede bulunan herhangi bir betik altyapısında profil oluşturma başladıktan sonra çağrılmalıdır. Yöntemi herhangi bir betik altyapısı için çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptprofilercontrol2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 Arabirimi](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)