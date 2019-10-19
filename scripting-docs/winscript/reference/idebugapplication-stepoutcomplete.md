---
title: 'IDebugApplication:: Stepouttamamlanmıştır | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f50d7e8a8936e52f4177450e7d163c4cfeaa55df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571044"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
İşlem hata ayıklama yöneticisine, tek adımlı moddaki bir dil altyapısının çağırana dönmek üzere olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dil motorları, bu yöntemi çağıranlarına geri dönmeden hemen önce tek adımlı modda çağırır. İşlem hata ayıklama Yöneticisi, ilk fırsatta kesintiye uğramaları gereken diğer tüm betik altyapılarını bilgilendirmek için bu fırsatı kullanır. Bu teknik, çapraz dil adım modlarının uygulanma şekli olur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication Arabirimi](../../winscript/reference/idebugapplication-interface.md)