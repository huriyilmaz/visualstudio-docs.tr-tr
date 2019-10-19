---
title: 'IDebugApplication:: SynchronousCallInDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574584"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Çağıranın hata ayıklayıcı iş parçacığında kod çalıştırmasına yönelik bir mekanizma sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pptc`  
 'ndaki Çağrılacak nesne.  
  
 `dwParam1`  
 'ndaki @No__t_0 metoduna geçirilecek ilk parametre.  
  
 `dwParam2`  
 'ndaki @No__t_0 metoduna geçirilecek ikinci parametre.  
  
 `dwParam3`  
 'ndaki @No__t_0 metoduna geçirilecek üçüncü parametre.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Dil motorları ve konaklar, genellikle bu yöntemi tek iş parçacıklı uygulamalarının üzerine serbest iş parçacıklı nesneler uygulamak için kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)    
 [IDebugThreadCall Arabirimi](../../winscript/reference/idebugthreadcall-interface.md)