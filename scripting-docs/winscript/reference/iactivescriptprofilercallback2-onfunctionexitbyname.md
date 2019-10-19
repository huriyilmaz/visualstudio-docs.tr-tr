---
title: 'Iactivescriptprofilercallback2:: OnFunctionExitByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571626"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Profil Oluşturucu nesnesine, betik altyapısının Belge Nesne Modeli (DOM) işlev çağrısını çalıştırmayı tamamladığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwszFunctionName`  
 'ndaki Betik altyapısının çalışmasını bitirdiğinde işlevin adı.  
  
 `scriptType`  
 'ndaki İşlevin türü. Geçerli değerlerin açıklamaları için bkz. [PROFILER_SCRIPT_TYPE Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntemin dönüş değeri, betik altyapısı tarafından yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 DOM çağrıları için, betik altyapısı [ıactivescriptprofilercallback:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)çağırmak yerine bu yöntemi çağırır. Bunun nedeni, DOM 'daki çok sayıda benzersiz Yöntem ve özelliklerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptprofilercallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2 Arabirimi](../../winscript/reference/iactivescriptprofilercallback2-interface.md)