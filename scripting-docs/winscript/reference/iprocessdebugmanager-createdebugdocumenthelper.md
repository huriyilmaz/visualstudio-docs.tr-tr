---
title: 'Iprocessdebugmanager:: Createdebugbelgeadı | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a009fa5174ab897116c02b91e376e2dc41d67600
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577101"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Bu uygulama için yeni bir hata ayıklama belgesi Yardımcısı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `punkOuter`  
 'ndaki Döndürülen nesne toplanırsa, `punkOuter` denetim `IUnknown` bir arabirim işaretçisidir. Aksi halde, null bir işaretçisidir.  
  
 `pddh`  
 dışı Bu uygulama için hata ayıklama belgesi yardımcı nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu uygulama için yeni bir hata ayıklama belgesi Yardımcısı oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IProcessDebugManager Arabirimi](../../winscript/reference/iprocessdebugmanager-interface.md)