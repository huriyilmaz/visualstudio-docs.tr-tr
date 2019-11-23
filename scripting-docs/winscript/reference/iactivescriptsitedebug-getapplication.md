---
title: 'Iactivescriptsitedebug:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2ad81e3b6b1707f5a23271cf0abe3832266c07f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570132"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
Bu betik sitesiyle ilişkili hata ayıklama uygulama nesnesini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppda`  
 dışı Betik sitesiyle ilişkili hata ayıklama uygulaması nesnesine yönelik işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Konak, hata ayıklamayı doğrudan desteklemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetApplication` yöntemi, bir akıllı ana bilgisayarın her bir Betiğin ait olduğu uygulama nesnesini tanımlamak için bir yol sağlar. Komut dosyası motorları bu yöntemi, sahip olduğu uygulamaları almak için çağırmayı denemelidir ve bu başarısız olursa `IProcessDebugManager::GetDefaultApplication`.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptsitedebug arabirimi](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)