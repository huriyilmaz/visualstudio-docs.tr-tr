---
title: 'Idebugsyncoperation:: Execute | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25da02e6736cc2f8ac27c82f922bd515e791bef1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576689"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Zaman uyumlu olarak işlemi gerçekleştirir ve döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppunkResult`  
 dışı İşlem tarafından döndürülen nesne parametresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_ABORT`|@No__t_0 yöntemi çağrılırken işlem iptal edildi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hedef iş parçacığında Işlem hata ayıklama Yöneticisi `Execute` yöntemini eşzamanlı olarak çağırır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugSyncOperation Arabirimi](../../winscript/reference/idebugsyncoperation-interface.md)