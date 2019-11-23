---
title: 'Idebugapplicationthread:: SynchronousCallIntoThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574493"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Çağıranın uygulama iş parçacığında kod çalıştırmasına yönelik bir mekanizma sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstcb`  
 'ndaki Çağrılacak nesne.  
  
 `dwParam1`  
 'ndaki `IDebugThreadCall::ThreadCallHandler` metoduna geçirilecek ilk parametre.  
  
 `dwParam2`  
 'ndaki `IDebugThreadCall::ThreadCallHandler` metoduna geçirilecek ikinci parametre.  
  
 `dwParam3`  
 'ndaki `IDebugThreadCall::ThreadCallHandler` metoduna geçirilecek üçüncü parametre.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, çağıranın hata ayıklayıcı iş parçacığında kod çalıştırmasına yönelik bir mekanizma sağlar. Dil motorları ve konaklar, genellikle bu yöntemi tek iş parçacıklı uygulamalarının üzerine serbest iş parçacıklı nesneler uygulamak için kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Idebugapplicationthread arabirimi](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall Arabirimi](../../winscript/reference/idebugthreadcall-interface.md)