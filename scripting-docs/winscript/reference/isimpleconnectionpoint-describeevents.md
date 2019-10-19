---
title: Iımpliconnectionpoint::D escribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571813"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Belirtilen olay aralığındaki her olay için DISPID ve adı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `iEvent`  
 'ndaki Alınacak ilk olayın dizini.  
  
 `cEvents`  
 'ndaki Alınacak olay sayısı.  
  
 `prgid`  
 dışı Olay PID değerleri dizisi.  
  
 `prgbstr`  
 dışı Olay adları dizisi.  
  
 `pcEventsFetched`  
 dışı Getirilen gerçek olay sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`S_FALSE`|Kullanılabilir olandan daha fazla olay istendi. Kullanılamayan olaylar DISPID_NULL ve null BSTR ile temsil edilir.|  
|`E_INVALIDARG`|Hiçbir öğe getirilemedi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, belirtilen olay aralığındaki her bir olay için DISPID ve adı döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ISimpleConnectionPoint Arabirimi](../../winscript/reference/isimpleconnectionpoint-interface.md)