---
title: 'Idağılım ROR:: GetNext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81186e6eba7983a1210e5de5bca5d83dd77089da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573111"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Sonraki `IDispError` nesnesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppde`  
 dışı Next `IDispError` nesnesini belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, sonraki `IDispError` nesnesini alır. Bu son `IDispError` nesnese, bu yöntem NULL değerini döndürür.  
  
> [!NOTE]
> Bu yöntem uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispError Arabirimi](../../winscript/reference/idisperror-interface.md)