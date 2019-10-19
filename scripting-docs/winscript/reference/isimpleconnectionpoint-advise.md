---
title: 'Iımpliconnectionpoint:: Advise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571833"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Basit bağlantı noktası nesnesi ile istemci havuzu arasında bir bağlantı kurar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdisp`  
 'ndaki İstemcinin öneri havuzunda `IDispatch` arabirimine yönelik işaretçi. İstemci havuzu, basit bağlantı noktasından giden çağrıları alır.  
  
 `pdwCookie`  
 dışı Bu bağlantıyı benzersiz bir şekilde tanımlayan döndürülen belirtecin işaretçisi. Çağıran, `ISimpleConnectionPoint::Unadvise` yöntemine geçirerek bağlantıyı silmek için bu belirteci daha sonra kullanır. Bağlantı başarıyla kurulmazsa, bu değer sıfırdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, basit bağlantı noktası nesnesi ile istemci havuzu arasında bir bağlantı kurar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iımpliconnectionpoint arabirimi](../../winscript/reference/isimpleconnectionpoint-interface.md)    
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)