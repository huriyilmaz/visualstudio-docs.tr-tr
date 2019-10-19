---
title: 'Iactivescriptprofilercallback:: kapanıyor | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571650"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Bir betik altyapısında profil oluşturma durdurulduğunda profil oluşturucu nesnesine bildirmek için çağırılır. Bu şekilde, profil oluşturucu nesnesi gerekirse Temizleme yordamlarını çağırabilir. Bu yöntem, komut dosyası altyapısı kapatılırken veya [ıactivescriptprofilercallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) öğesine yapılan bir çağrı başarısız olduğunda betik altyapısı tarafından da çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hrReason`  
 'ndaki Kapatma nedeni. Betik altyapısı kapanmakta ise `S_OK` geçirilir. [Iactivescriptprofilercallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) çağrısı HRESULT bir hata döndürürse HRESULT geçirilir. Aksi takdirde, bu değer [ıactivescriptprofilercontrol:: Stopprofilleme](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)öğesinden alınır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri, betik altyapısı tarafından yok sayılır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptProfilerCallback Arabirimi](../../winscript/reference/iactivescriptprofilercallback-interface.md)