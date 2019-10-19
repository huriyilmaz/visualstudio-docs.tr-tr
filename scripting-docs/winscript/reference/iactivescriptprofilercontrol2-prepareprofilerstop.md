---
title: Iactivescriptprofilercontrol2::P repareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571436"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Profil oluşturucuyu, tüm uygulanabilir komut dosyası altyapılarında profil oluşturmayı durduramayacağız bildirir. Bu yöntemi kullanarak, profil oluşturmayı durdurduğunuzda [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] çalışıyorsa, tüm çağrı yığınını elde edebilirsiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yöntem herhangi bir parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Profil oluşturma başlatılamadı.|  
|`S_FALSE`|Bir betik çalışmadığı zaman profil oluşturma işlemi durduruldu.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profil oluşturma etkin değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 çağırmak, Çağrı yığınındaki işlevler için olayların gönderilmesini sağlar. Bu yöntem, geçerli sekmede bulunan herhangi bir betik altyapısında profil oluşturmayı durdurmadan önce çağrılmalıdır. Yöntemi herhangi bir betik altyapısı için çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptprofilercontrol2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)    
 [IActiveScriptProfilerControl2 Arabirimi](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)