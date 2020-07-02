---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 0b82ab6cd37f789e98ca08c635011a7e04f5b871
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835634"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Bu betik sitesiyle ilişkili hata ayıklama uygulama nesnesini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppda`  
 dışı Betik sitesiyle ilişkili hata ayıklama uygulaması nesnesine yönelik işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi döndürür `HRESULT` . Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Description|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_NOTIMPL`|Konak, hata ayıklamayı doğrudan desteklemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetApplication`Yöntemi, bir akıllı ana bilgisayarın her bir Betiğin ait olduğu uygulama nesnesini tanımlamak için bir yol sağlar. Komut dosyası motorları bu yöntemi çağırmak için bu yöntemi çağırmayı denemelidir `IProcessDebugManager::GetDefaultApplication` .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IActiveScriptSiteDebug32 arabirimi](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)