---
title: 'Idebugapplicationthread:: Queryısdebuggerthread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsDebuggerThread
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: febce73e2c40d0df02acc42f6219eca30afb3f29
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574538"
---
# <a name="idebugapplicationthreadqueryisdebuggerthread"></a>IDebugApplicationThread::QueryIsDebuggerThread
Bu iş parçacığının hata ayıklayıcı iş parçacığı olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT QueryIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Bu yöntem hiçbir parametre alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntemi başarılı oldu ve hata ayıklayıcı iş parçacığı.|  
|`S_FALSE`|Bu, hata ayıklayıcı iş parçacığı değildir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bu iş parçacığının hata ayıklayıcı iş parçacığı olup olmadığını belirler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplicationThread Arabirimi](../../winscript/reference/idebugapplicationthread-interface.md)