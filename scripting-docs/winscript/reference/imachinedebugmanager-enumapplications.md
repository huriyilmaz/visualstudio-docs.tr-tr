---
title: 'Imachinedebugmanager:: Trmapplications | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::EnumApplications
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518e7fd2f22a89e767dec7cc2c7b03ab811b2904
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573948"
---
# <a name="imachinedebugmanagerenumapplications"></a>IMachineDebugManager::EnumApplications
Çalışan uygulamaların geçerli listesinin bir Numaralandırıcı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppeda`  
 dışı Çalışan uygulamaların geçerli listesini içeren Numaralandırıcı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, çalışan uygulamaların geçerli listesinin bir Numaralandırıcı döndürür. Hata ayıklayıcı IDE, hata ayıklama amacıyla uygulamaları göstermek ve eklemek için bu yöntemi kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IMachineDebugManager Arabirimi](../../winscript/reference/imachinedebugmanager-interface.md)