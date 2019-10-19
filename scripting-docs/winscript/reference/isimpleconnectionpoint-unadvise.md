---
title: 'Iımpliconnectionpoint:: Unadvise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571755"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Daha önce `ISimpleConnectionPoint::Advise` aracılığıyla kurulan bir danışmanlık bağlantısını sonlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwCookie`  
 'ndaki @No__t_0 'den döndürülen sonlandırılacak bağlantı belirteci.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir danışmanlık bağlantısı sonlandırıldığında, bağlantı noktası `ISimpleConnectionPoint::Advise` yöntemi sırasında bağlantı için kaydedilen işaretçiye `Release` yöntemini çağırır. Bu çağrı, bağlantı noktası danışmanlık havuzunun `QueryInterface` çağırdığında `ISimpleConnectionPoint::Advise` sırasında gerçekleştirilen `AddRef` tersine çevirir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ISimpleConnectionPoint Arabirimi](../../winscript/reference/isimpleconnectionpoint-interface.md)