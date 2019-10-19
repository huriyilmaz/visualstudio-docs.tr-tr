---
title: 'Iobjectıdentity:: ısequalobject | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571469"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Nesnenin geçerli nesneye eşit olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `punk`  
 'ndaki Geçerli nesneyle Karşılaştırılacak nesnenin adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Nesneler eşittir.|  
|`S_FALSE`|Nesneler eşit değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 yönteminin uygulanması, yalnızca nesneler aynıysa `S_OK` döndürmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IObjectIdentity Arabirimi](../../winscript/reference/iobjectidentity-interface.md)