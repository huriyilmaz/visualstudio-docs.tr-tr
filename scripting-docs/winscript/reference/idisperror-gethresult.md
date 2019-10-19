---
title: 'Idağılım ROR:: GetHresult | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHresult
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62661e14c36881ca83763c277dbfd5385f192fb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573120"
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
@No__t_0 nesnesinden hata kodunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phr`  
 dışı Hata kodunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, `IDispError` nesnesinden hata kodunu alır.  
  
> [!NOTE]
> Bu yöntem uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispError Arabirimi](../../winscript/reference/idisperror-interface.md)