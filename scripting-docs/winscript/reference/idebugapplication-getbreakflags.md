---
title: 'IDebugApplication:: GetBreakFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetBreakFlags
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetBreakFlags
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a614429ebb8cc9271a0444536d14c45b69a9588f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574982"
---
# <a name="idebugapplicationgetbreakflags"></a>IDebugApplication::GetBreakFlags
Uygulamanın geçerli kesme bayraklarını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pabf`  
 dışı Uygulamanın geçerli kesme bayrakları.  
  
 `pprdatSteppingThread`  
 dışı Çalışmakta olan iş parçacığı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT`döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, uygulamanın geçerli kesme bayraklarını döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugApplication arabirimi](../../winscript/reference/idebugapplication-interface.md)   
 [APPBREAKFLAGS Sabit Listesi](../../winscript/reference/appbreakflags-enumeration.md)