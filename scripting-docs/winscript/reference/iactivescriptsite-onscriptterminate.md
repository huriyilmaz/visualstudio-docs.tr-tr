---
title: 'IActiveScriptSite:: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570209"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Ana bilgisayara betiğin yürütmeyi tamamladığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pvarResult`  
 'ndaki Betik sonucunu içeren bir değişkenin adresi veya betik sonuç üretmez `NULL`.  
  
 `pexcepinfo`  
 'ndaki Komut dosyası sonlandırıldığında oluşturulan özel durum bilgilerini içeren `EXCEPINFO` yapısının adresi veya hiçbir özel durum oluşturulmadığından `NULL`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa `S_OK` döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Betik altyapısı, [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) yöntemine yapılan ÇAĞRıDAN önce SCRIPTSTATE_INITIALIZED bayrağı ayarlanmış olarak bu yöntemi çağırır. Bu yöntem, ana bilgisayara tamamlanma durumu ve sonuçları döndürmek için kullanılabilir. Konaktan gelen olayları temel alan çok sayıda betik dilinin, ana bilgisayar tarafından tanımlanan yaşam yaymaların olduğunu unutmayın. Bu durumda, bu yöntem hiçbir şekilde çağrılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)