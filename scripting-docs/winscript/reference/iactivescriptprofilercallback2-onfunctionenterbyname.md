---
title: 'Iactivescriptprofilercallback2:: OnFunctionEnterByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571632"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Profil Oluşturucu nesnesine, betik altyapısının bir Belge Nesne Modeli (DOM) işlev çağrısını yürütemeyeceğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwszFunctionName`  
 'ndaki Betik altyapısının yürütecağı işlevin adı.  
  
 `scriptType`  
 'ndaki İşlevin türü. Geçerli değerlerin açıklamaları için bkz. [PROFILER_SCRIPT_TYPE numaralandırması](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri, betik altyapısı tarafından yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 DOM çağrıları için, betik altyapısı [ıactivescriptprofilercallback:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)' ı çağırmak yerine bu yöntemi çağırır. Bunun nedeni, DOM 'daki çok sayıda benzersiz Yöntem ve özelliklerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptprofilercallback2:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2 Arabirimi](../../winscript/reference/iactivescriptprofilercallback2-interface.md)