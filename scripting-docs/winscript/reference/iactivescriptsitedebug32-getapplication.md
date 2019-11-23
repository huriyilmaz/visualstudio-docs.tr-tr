---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572192"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32:: GetApplication
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
 [IActiveScriptSiteDebug32 arabirimi](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)